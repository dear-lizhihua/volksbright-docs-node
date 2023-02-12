#### `readableStreamBYOBReader.closed`

<!-- YAML
added: v16.5.0
-->

* Type: {Promise} Fulfilled with `undefined` when the associated
  {ReadableStream} is closed or rejected if the stream errors or the reader's
  lock is released before the stream finishes closing.
