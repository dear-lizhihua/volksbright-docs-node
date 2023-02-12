#### `URL.revokeObjectURL(id)`

<!-- YAML
added: v16.7.0
-->

> Stability: 1 - Experimental

* `id` {string} A `'blob:nodedata:...` URL string returned by a prior call to
  `URL.createObjectURL()`.

Removes the stored {Blob} identified by the given ID. Attempting to revoke a
ID that isn't registered will silently fail.
