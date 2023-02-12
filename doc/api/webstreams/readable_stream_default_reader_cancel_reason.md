#### `readableStreamDefaultReader.cancel([reason])`

<!-- YAML
added: v16.5.0
-->

* `reason` {any}
* Returns: A promise fulfilled with `undefined`.

Cancels the {ReadableStream} and returns a promise that is fulfilled
when the underlying stream has been canceled.
