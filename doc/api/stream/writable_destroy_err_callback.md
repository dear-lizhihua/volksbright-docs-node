#### `writable._destroy(err, callback)`

<!-- YAML
added: v8.0.0
-->

* `err` {Error} A possible error.
* `callback` {Function} A callback function that takes an optional error
  argument.

The `_destroy()` method is called by [`writable.destroy()`][writable-destroy].
It can be overridden by child classes but it **must not** be called directly.
Furthermore, the `callback` should not be mixed with async/await
once it is executed when a promise is resolved.
