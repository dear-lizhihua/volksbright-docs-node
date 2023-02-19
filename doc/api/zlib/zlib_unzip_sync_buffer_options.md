### `zlib.unzipSync(buffer[, options])`

<!-- YAML
added: v0.11.12
changes:
  - version: v9.4.0
    pr-url: https://github.com/nodejs/node/pull/16042
    description: The `buffer` parameter can be an `ArrayBuffer`.
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/12223
    description: The `buffer` parameter can be any `TypedArray` or `DataView`.
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/12001
    description: The `buffer` parameter can be an `Uint8Array` now.
-->

* `buffer` {Buffer|TypedArray|DataView|ArrayBuffer|string}
* `options` {zlib options}

Decompress a chunk of data with [`Unzip`][].

[Brotli parameters]: #brotli-constants
[Memory usage tuning]: #memory-usage-tuning
[RFC 7932]: https://www.rfc-editor.org/rfc/rfc7932.txt
[Streams API]: stream.md
[`.flush()`]: #zlibflushkind-callback
[`Accept-Encoding`]: https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.3
[`ArrayBuffer`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer
[`BrotliCompress`]: #class-zlibbrotlicompress
[`BrotliDecompress`]: #class-zlibbrotlidecompress
[`Buffer`]: buffer.md#class-buffer
[`Content-Encoding`]: https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.11
[`DataView`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/DataView
[`DeflateRaw`]: #class-zlibdeflateraw
[`Deflate`]: #class-zlibdeflate
[`Gunzip`]: #class-zlibgunzip
[`Gzip`]: #class-zlibgzip
[`InflateRaw`]: #class-zlibinflateraw
[`Inflate`]: #class-zlibinflate
[`TypedArray`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray
[`Unzip`]: #class-zlibunzip
[`buffer.kMaxLength`]: buffer.md#bufferkmaxlength
[`deflateInit2` and `inflateInit2`]: https://zlib.net/manual.html#Advanced
[`stream.Transform`]: stream.md#class-streamtransform
[`zlib.bytesWritten`]: #zlibbyteswritten
[convenience methods]: #convenience-methods
[zlib documentation]: https://zlib.net/manual.html#Constants
[zlib.createGzip example]: #zlib
