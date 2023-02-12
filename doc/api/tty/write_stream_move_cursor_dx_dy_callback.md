### `writeStream.moveCursor(dx, dy[, callback])`

<!-- YAML
added: v0.7.7
changes:
  - version: v12.7.0
    pr-url: https://github.com/nodejs/node/pull/28721
    description: The stream's write() callback and return value are exposed.
-->

* `dx` {number}
* `dy` {number}
* `callback` {Function} Invoked once the operation completes.
* Returns: {boolean} `false` if the stream wishes for the calling code to wait
  for the `'drain'` event to be emitted before continuing to write additional
  data; otherwise `true`.

`writeStream.moveCursor()` moves this `WriteStream`'s cursor _relative_ to its
current position.
