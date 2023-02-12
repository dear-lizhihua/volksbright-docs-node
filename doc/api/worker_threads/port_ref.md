### `port.ref()`

<!-- YAML
added: v10.5.0
-->

Opposite of `unref()`. Calling `ref()` on a previously `unref()`ed port does
_not_ let the program exit if it's the only active handle left (the default
behavior). If the port is `ref()`ed, calling `ref()` again has no effect.

If listeners are attached or removed using `.on('message')`, the port
is `ref()`ed and `unref()`ed automatically depending on whether
listeners for the event exist.
