### `socket.close([callback])`

<!-- YAML
added: v0.1.99
-->

* `callback` {Function} Called when the socket has been closed.

Close the underlying socket and stop listening for data on it. If a callback is
provided, it is added as a listener for the [`'close'`][] event.
