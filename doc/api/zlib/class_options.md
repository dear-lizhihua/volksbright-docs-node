## Class: `Options`

<!-- YAML
added: v0.11.1
changes:
  - version:
    - v14.5.0
    - v12.19.0
    pr-url: https://github.com/nodejs/node/pull/33516
    description: The `maxOutputLength` option is supported now.
  - version: v9.4.0
    pr-url: https://github.com/nodejs/node/pull/16042
    description: The `dictionary` option can be an `ArrayBuffer`.
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/12001
    description: The `dictionary` option can be an `Uint8Array` now.
  - version: v5.11.0
    pr-url: https://github.com/nodejs/node/pull/6069
    description: The `finishFlush` option is supported now.
-->

<!--type=misc-->

Each zlib-based class takes an `options` object. No options are required.

Some options are only relevant when compressing and are
ignored by the decompression classes.

* `flush` {integer} **Default:** `zlib.constants.Z_NO_FLUSH`
* `finishFlush` {integer} **Default:** `zlib.constants.Z_FINISH`
* `chunkSize` {integer} **Default:** `16 * 1024`
* `windowBits` {integer}
* `level` {integer} (compression only)
* `memLevel` {integer} (compression only)
* `strategy` {integer} (compression only)
* `dictionary` {Buffer|TypedArray|DataView|ArrayBuffer} (deflate/inflate only,
  empty dictionary by default)
* `info` {boolean} (If `true`, returns an object with `buffer` and `engine`.)
* `maxOutputLength` {integer} Limits output size when using
  [convenience methods][]. **Default:** [`buffer.kMaxLength`][]

See the [`deflateInit2` and `inflateInit2`][] documentation for more
information.
