### `stream.Duplex.from(src)`

<!-- YAML
added: v16.8.0
changes:
  - version: v19.5.0
    pr-url: https://github.com/nodejs/node/pull/46190
    description: The `src` argument can now be a `ReadableStream` or
                 `WritableStream`.
-->

* `src` {Stream|Blob|ArrayBuffer|string|Iterable|AsyncIterable|
  AsyncGeneratorFunction|AsyncFunction|Promise|Object|
  ReadableStream|WritableStream}

A utility method for creating duplex streams.

* `Stream` converts writable stream into writable `Duplex` and readable stream
  to `Duplex`.
* `Blob` converts into readable `Duplex`.
* `string` converts into readable `Duplex`.
* `ArrayBuffer` converts into readable `Duplex`.
* `AsyncIterable` converts into a readable `Duplex`. Cannot yield
  `null`.
* `AsyncGeneratorFunction` converts into a readable/writable transform
  `Duplex`. Must take a source `AsyncIterable` as first parameter. Cannot yield
  `null`.
* `AsyncFunction` converts into a writable `Duplex`. Must return
  either `null` or `undefined`
* `Object ({ writable, readable })` converts `readable` and
  `writable` into `Stream` and then combines them into `Duplex` where the
  `Duplex` will write to the `writable` and read from the `readable`.
* `Promise` converts into readable `Duplex`. Value `null` is ignored.
* `ReadableStream` converts into readable `Duplex`.
* `WritableStream` converts into writable `Duplex`.
* Returns: {stream.Duplex}

If an `Iterable` object containing promises is passed as an argument,
it might result in unhandled rejection.

```js
const { Duplex } = require('node:stream');

Duplex.from([
  new Promise((resolve) => setTimeout(resolve('1'), 1500)),
  new Promise((_, reject) => setTimeout(reject(new Error('2')), 1000)), // Unhandled rejection
]);
```
