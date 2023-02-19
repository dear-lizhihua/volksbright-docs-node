### `zlib.flush([kind, ]callback)`

<!-- YAML
added: v0.5.8
-->

* `kind` **Default:** `zlib.constants.Z_FULL_FLUSH` for zlib-based streams,
  `zlib.constants.BROTLI_OPERATION_FLUSH` for Brotli-based streams.
* `callback` {Function}

Flush pending data. Don't call this frivolously, premature flushes negatively
impact the effectiveness of the compression algorithm.

Calling this only flushes data from the internal `zlib` state, and does not
perform flushing of any kind on the streams level. Rather, it behaves like a
normal call to `.write()`, i.e. it will be queued up behind other pending
writes and will only produce output when data is being read from the stream.
