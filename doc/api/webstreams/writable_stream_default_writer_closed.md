#### `writableStreamDefaultWriter.closed`

<!-- YAML
added: v16.5.0
-->

* Type: {Promise} Fulfilled with `undefined` when the associated
  {WritableStream} is closed or rejected if the stream errors or the writer's
  lock is released before the stream finishes closing.
