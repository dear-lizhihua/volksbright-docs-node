## Class: `tty.WriteStream`

<!-- YAML
added: v0.5.8
-->

* Extends: {net.Socket}

Represents the writable side of a TTY. In normal circumstances,
[`process.stdout`][] and [`process.stderr`][] will be the only
`tty.WriteStream` instances created for a Node.js process and there
should be no reason to create additional instances.
