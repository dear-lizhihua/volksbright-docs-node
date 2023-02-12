### `stream.Readable.toWeb(streamReadable[, options])`

<!-- YAML
added: v17.0.0
-->

> Stability: 1 - Experimental

* `streamReadable` {stream.Readable}
* `options` {Object}
  * `strategy` {Object}
    * `highWaterMark` {number}
    * `size` {Function}
* Returns: {ReadableStream}
