### `worker.unref()`

<!-- YAML
added: v10.5.0
-->

Calling `unref()` on a worker allows the thread to exit if this is the only
active handle in the event system. If the worker is already `unref()`ed calling
`unref()` again has no effect.
