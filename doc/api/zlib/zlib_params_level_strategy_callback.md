### `zlib.params(level, strategy, callback)`

<!-- YAML
added: v0.11.4
-->

* `level` {integer}
* `strategy` {integer}
* `callback` {Function}

This function is only available for zlib-based streams, i.e. not Brotli.

Dynamically update the compression level and compression strategy.
Only applicable to deflate algorithm.
