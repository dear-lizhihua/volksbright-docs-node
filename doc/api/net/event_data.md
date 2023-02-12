### Event: `'data'`

<!-- YAML
added: v0.1.90
-->

* {Buffer|string}

Emitted when data is received. The argument `data` will be a `Buffer` or
`String`. Encoding of data is set by [`socket.setEncoding()`][].

The data will be lost if there is no listener when a `Socket`
emits a `'data'` event.
