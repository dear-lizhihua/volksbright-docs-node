### `outgoingMessage.writableHighWaterMark`

<!-- YAML
added: v12.9.0
-->

* {number}

The `highWaterMark` of the underlying socket if assigned. Otherwise, the default
buffer level when [`writable.write()`][] starts returning false (`16384`).
