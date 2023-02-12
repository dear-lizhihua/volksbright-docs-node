## `process.constrainedMemory()`

<!-- YAML
added: v19.6.0
-->

> Stability: 1 - Experimental

* {number|undefined}

Gets the amount of memory available to the process (in bytes) based on
limits imposed by the OS. If there is no such constraint, or the constraint
is unknown, `undefined` is returned.

See [`uv_get_constrained_memory`][uv_get_constrained_memory] for more
information.
