### `socket.address()`

<!-- YAML
added: v0.1.99
-->

* Returns: {Object}

Returns an object containing the address information for a socket.
For UDP sockets, this object will contain `address`, `family`, and `port`
properties.

This method throws `EBADF` if called on an unbound socket.
