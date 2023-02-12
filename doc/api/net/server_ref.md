### `server.ref()`

<!-- YAML
added: v0.9.1
-->

* Returns: {net.Server}

Opposite of `unref()`, calling `ref()` on a previously `unref`ed server will
_not_ let the program exit if it's the only server left (the default behavior).
If the server is `ref`ed calling `ref()` again will have no effect.
