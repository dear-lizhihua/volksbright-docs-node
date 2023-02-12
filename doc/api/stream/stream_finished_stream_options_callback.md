### `stream.finished(stream[, options], callback)`

<!-- YAML
added: v10.0.0
changes:
  - version: v19.5.0
    pr-url: https://github.com/nodejs/node/pull/46205
    description: Added support for `ReadableStream` and `WritableStream`.
  - version: v15.11.0
    pr-url: https://github.com/nodejs/node/pull/37354
    description: The `signal` option was added.
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/32158
    description: The `finished(stream, cb)` will wait for the `'close'` event
                 before invoking the callback. The implementation tries to
                 detect legacy streams and only apply this behavior to streams
                 which are expected to emit `'close'`.
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/31545
    description: Emitting `'close'` before `'end'` on a `Readable` stream
                 will cause an `ERR_STREAM_PREMATURE_CLOSE` error.
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/31509
    description: Callback will be invoked on streams which have already
                 finished before the call to `finished(stream, cb)`.
-->

* `stream` {Stream|ReadableStream|WritableStream}

A readable and/or writable stream/webstream.

* `options` {Object}
  * `error` {boolean} If set to `false`, then a call to `emit('error', err)` is
    not treated as finished. **Default:** `true`.
  * `readable` {boolean} When set to `false`, the callback will be called when
    the stream ends even though the stream might still be readable.
    **Default:** `true`.
  * `writable` {boolean} When set to `false`, the callback will be called when
    the stream ends even though the stream might still be writable.
    **Default:** `true`.
  * `signal` {AbortSignal} allows aborting the wait for the stream finish. The
    underlying stream will _not_ be aborted if the signal is aborted. The
    callback will get called with an `AbortError`. All registered
    listeners added by this function will also be removed.
  * `cleanup` {boolean} remove all registered stream listeners.
    **Default:** `false`.

* `callback` {Function} A callback function that takes an optional error
  argument.

* Returns: {Function} A cleanup function which removes all registered
  listeners.

A function to get notified when a stream is no longer readable, writable
or has experienced an error or a premature close event.

```js
const { finished } = require('node:stream');
const fs = require('node:fs');

const rs = fs.createReadStream('archive.tar');

finished(rs, (err) => {
  if (err) {
    console.error('Stream failed.', err);
  } else {
    console.log('Stream is done reading.');
  }
});

rs.resume(); // Drain the stream.
```

Especially useful in error handling scenarios where a stream is destroyed
prematurely (like an aborted HTTP request), and will not emit `'end'`
or `'finish'`.

The `finished` API provides [promise version][stream-finished-promise].

`stream.finished()` leaves dangling event listeners (in particular
`'error'`, `'end'`, `'finish'` and `'close'`) after `callback` has been
invoked. The reason for this is so that unexpected `'error'` events (due to
incorrect stream implementations) do not cause unexpected crashes.
If this is unwanted behavior then the returned cleanup function needs to be
invoked in the callback:

```js
const cleanup = finished(rs, (err) => {
  cleanup();
  // ...
});
```
