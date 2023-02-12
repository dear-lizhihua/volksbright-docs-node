### `socket.setRecvBufferSize(size)`

<!-- YAML
added: v8.7.0
-->

* `size` {integer}

Sets the `SO_RCVBUF` socket option. Sets the maximum socket receive buffer
in bytes.

This method throws [`ERR_SOCKET_BUFFER_SIZE`][] if called on an unbound socket.
