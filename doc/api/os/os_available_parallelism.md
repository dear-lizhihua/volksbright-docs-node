## `os.availableParallelism()`

<!-- YAML
added:
  - v19.4.0
  - v18.14.0
-->

* Returns: {integer}

Returns an estimate of the default amount of parallelism a program should use.
Always returns a value greater than zero.

This function is a small wrapper about libuv's [`uv_available_parallelism()`][].
