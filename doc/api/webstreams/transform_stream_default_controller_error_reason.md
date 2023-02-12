#### `transformStreamDefaultController.error([reason])`

<!-- YAML
added: v16.5.0
-->

* `reason` {any}

Signals to both the readable and writable side that an error has occurred
while processing the transform data, causing both sides to be abruptly
closed.
