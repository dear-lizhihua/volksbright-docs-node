### `emitter.getMaxListeners()`

<!-- YAML
added: v1.0.0
-->

* Returns: {integer}

Returns the current max listener value for the `EventEmitter` which is either
set by [`emitter.setMaxListeners(n)`][] or defaults to
[`events.defaultMaxListeners`][].
