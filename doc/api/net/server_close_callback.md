### `server.close([callback])`

<!-- YAML
added: v0.1.90
-->

* `callback` {Function} Called when the server is closed.
* Returns: {net.Server}

Stops the server from accepting new connections and keeps existing
connections. This function is asynchronous, the server is finally closed
when all connections are ended and the server emits a [`'close'`][] event.
The optional `callback` will be called once the `'close'` event occurs. Unlike
that event, it will be called with an `Error` as its only argument if the server
was not open when it was closed.
