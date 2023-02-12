### `socket.setSendBufferSize(size)`

<!-- YAML
added: v8.7.0
-->

* `size` {integer}

Sets the `SO_SNDBUF` socket option. Sets the maximum socket send buffer
in bytes.

This method throws [`ERR_SOCKET_BUFFER_SIZE`][] if called on an unbound socket.
