### `outgoingMessage.pipe()`

<!-- YAML
added: v9.0.0
-->

Overrides the `stream.pipe()` method inherited from the legacy `Stream` class
which is the parent class of `http.OutgoingMessage`.

Calling this method will throw an `Error` because `outgoingMessage` is a
write-only stream.
