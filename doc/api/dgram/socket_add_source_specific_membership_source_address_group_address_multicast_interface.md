### `socket.addSourceSpecificMembership(sourceAddress, groupAddress[, multicastInterface])`

<!-- YAML
added:
 - v13.1.0
 - v12.16.0
-->

* `sourceAddress` {string}
* `groupAddress` {string}
* `multicastInterface` {string}

Tells the kernel to join a source-specific multicast channel at the given
`sourceAddress` and `groupAddress`, using the `multicastInterface` with the
`IP_ADD_SOURCE_MEMBERSHIP` socket option. If the `multicastInterface` argument
is not specified, the operating system will choose one interface and will add
membership to it. To add membership to every available interface, call
`socket.addSourceSpecificMembership()` multiple times, once per interface.

When called on an unbound socket, this method will implicitly bind to a random
port, listening on all interfaces.
