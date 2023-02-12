#### `writableStreamDefaultWriter.abort([reason])`

<!-- YAML
added: v16.5.0
-->

* `reason` {any}
* Returns: A promise fulfilled with `undefined`.

Abruptly terminates the `WritableStream`. All queued writes will be
canceled with their associated promises rejected.
