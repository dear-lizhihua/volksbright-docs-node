### `buffer.resolveObjectURL(id)`

<!-- YAML
added: v16.7.0
-->

> Stability: 1 - Experimental

* `id` {string} A `'blob:nodedata:...` URL string returned by a prior call to
  `URL.createObjectURL()`.
* Returns: {Blob}

Resolves a `'blob:nodedata:...'` an associated {Blob} object registered using
a prior call to `URL.createObjectURL()`.
