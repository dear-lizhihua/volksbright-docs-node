## Class: `tty.ReadStream`

<!-- YAML
added: v0.5.8
-->

* Extends: {net.Socket}

Represents the readable side of a TTY. In normal circumstances
[`process.stdin`][] will be the only `tty.ReadStream` instance in a Node.js
process and there should be no reason to create additional instances.
