#### `readableStream.pipeThrough(transform[, options])`

<!-- YAML
added: v16.5.0
-->

* `transform` {Object}
  * `readable` {ReadableStream} The `ReadableStream` to which
    `transform.writable` will push the potentially modified data
    is receives from this `ReadableStream`.
  * `writable` {WritableStream} The `WritableStream` to which this
    `ReadableStream`'s data will be written.
* `options` {Object}
  * `preventAbort` {boolean} When `true`, errors in this `ReadableStream`
    will not cause `transform.writable` to be aborted.
  * `preventCancel` {boolean} When `true`, errors in the destination
    `transform.writable` do not cause this `ReadableStream` to be
    canceled.
  * `preventClose` {boolean} When `true`, closing this `ReadableStream`
    does not cause `transform.writable` to be closed.
  * `signal` {AbortSignal} Allows the transfer of data to be canceled
    using an {AbortController}.
* Returns: {ReadableStream} From `transform.readable`.

Connects this {ReadableStream} to the pair of {ReadableStream} and
{WritableStream} provided in the `transform` argument such that the
data from this {ReadableStream} is written in to `transform.writable`,
possibly transformed, then pushed to `transform.readable`. Once the
pipeline is configured, `transform.readable` is returned.

Causes the `readableStream.locked` to be `true` while the pipe operation
is active.

```mjs
import {
  ReadableStream,
  TransformStream,
} from 'node:stream/web';

const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('a');
  },
});

const transform = new TransformStream({
  transform(chunk, controller) {
    controller.enqueue(chunk.toUpperCase());
  },
});

const transformedStream = stream.pipeThrough(transform);

for await (const chunk of transformedStream)
  console.log(chunk);
```

```cjs
const {
  ReadableStream,
  TransformStream,
} = require('node:stream/web');

const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('a');
  },
});

const transform = new TransformStream({
  transform(chunk, controller) {
    controller.enqueue(chunk.toUpperCase());
  },
});

const transformedStream = stream.pipeThrough(transform);

(async () => {
  for await (const chunk of transformedStream)
    console.log(chunk);
})();
```
