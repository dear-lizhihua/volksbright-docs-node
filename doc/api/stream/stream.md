# Stream

<!--introduced_in=v0.10.0-->

> Stability: 2 - Stable

<!-- source_link=lib/stream.js -->

A stream is an abstract interface for working with streaming data in Node.js.
The `node:stream` module provides an API for implementing the stream interface.

There are many stream objects provided by Node.js. For instance, a
[request to an HTTP server][http-incoming-message] and [`process.stdout`][]
are both stream instances.

Streams can be readable, writable, or both. All streams are instances of
[`EventEmitter`][].

To access the `node:stream` module:

```js
const stream = require('node:stream');
```

The `node:stream` module is useful for creating new types of stream instances.
It is usually not necessary to use the `node:stream` module to consume streams.
