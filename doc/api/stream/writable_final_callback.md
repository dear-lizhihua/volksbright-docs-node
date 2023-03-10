#### `writable._final(callback)`

<!-- YAML
added: v8.0.0
-->

* `callback` {Function} Call this function (optionally with an error
  argument) when finished writing any remaining data.

The `_final()` method **must not** be called directly. It may be implemented
by child classes, and if so, will be called by the internal `Writable`
class methods only.

This optional function will be called before the stream closes, delaying the
`'finish'` event until `callback` is called. This is useful to close resources
or write buffered data before a stream ends.
