#### `http2stream.pushStream(headers[, options], callback)`

<!-- YAML
added: v8.4.0
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41678
    description: Passing an invalid callback to the `callback` argument
                 now throws `ERR_INVALID_ARG_TYPE` instead of
                 `ERR_INVALID_CALLBACK`.
-->

* `headers` {HTTP/2 Headers Object}
* `options` {Object}
  * `exclusive` {boolean} When `true` and `parent` identifies a parent Stream,
    the created stream is made the sole direct dependency of the parent, with
    all other existing dependents made a dependent of the newly created stream.
    **Default:** `false`.
  * `parent` {number} Specifies the numeric identifier of a stream the newly
    created stream is dependent on.
* `callback` {Function} Callback that is called once the push stream has been
  initiated.
  * `err` {Error}
  * `pushStream` {ServerHttp2Stream} The returned `pushStream` object.
  * `headers` {HTTP/2 Headers Object} Headers object the `pushStream` was
    initiated with.

Initiates a push stream. The callback is invoked with the new `Http2Stream`
instance created for the push stream passed as the second argument, or an
`Error` passed as the first argument.

```js
const http2 = require('node:http2');
const server = http2.createServer();
server.on('stream', (stream) => {
  stream.respond({ ':status': 200 });
  stream.pushStream({ ':path': '/' }, (err, pushStream, headers) => {
    if (err) throw err;
    pushStream.respond({ ':status': 200 });
    pushStream.end('some pushed data');
  });
  stream.end('some data');
});
```

Setting the weight of a push stream is not allowed in the `HEADERS` frame. Pass
a `weight` value to `http2stream.priority` with the `silent` option set to
`true` to enable server-side bandwidth balancing between concurrent streams.

Calling `http2stream.pushStream()` from within a pushed stream is not permitted
and will throw an error.
