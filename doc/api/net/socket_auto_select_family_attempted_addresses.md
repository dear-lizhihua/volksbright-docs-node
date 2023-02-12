### `socket.autoSelectFamilyAttemptedAddresses`

<!-- YAML
added: v19.4.0
-->

* {string\[]}

This property is only present if the family autoselection algorithm is enabled in
[`socket.connect(options)`][] and it is an array of the addresses that have been attempted.

Each address is a string in the form of `$IP:$PORT`. If the connection was successful,
then the last address is the one that the socket is currently connected to.
