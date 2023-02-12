#### `readableStreamDefaultReader.read()`

<!-- YAML
added: v16.5.0
-->

* Returns: A promise fulfilled with an object:
  * `value` {ArrayBuffer}
  * `done` {boolean}

Requests the next chunk of data from the underlying {ReadableStream}
and returns a promise that is fulfilled with the data once it is
available.
