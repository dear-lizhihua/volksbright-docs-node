### `socket.destroy([error])`

<!-- YAML
added: v0.1.90
-->

* `error` {Object}
* Returns: {net.Socket}

Ensures that no more I/O activity happens on this socket.
Destroys the stream and closes the connection.

See [`writable.destroy()`][] for further details.
