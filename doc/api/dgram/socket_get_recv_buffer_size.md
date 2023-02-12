### `socket.getRecvBufferSize()`

<!-- YAML
added: v8.7.0
-->

* Returns: {number} the `SO_RCVBUF` socket receive buffer size in bytes.

This method throws [`ERR_SOCKET_BUFFER_SIZE`][] if called on an unbound socket.
