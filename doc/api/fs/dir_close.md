#### `dir.close()`

<!-- YAML
added: v12.12.0
-->

* Returns: {Promise}

Asynchronously close the directory's underlying resource handle.
Subsequent reads will result in errors.

A promise is returned that will be resolved after the resource has been
closed.
