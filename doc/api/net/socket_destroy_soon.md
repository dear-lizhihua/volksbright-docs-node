### `socket.destroySoon()`

<!-- YAML
added: v0.3.4
-->

Destroys the socket after all data is written. If the `'finish'` event was
already emitted the socket is destroyed immediately. If the socket is still
writable it implicitly calls `socket.end()`.
