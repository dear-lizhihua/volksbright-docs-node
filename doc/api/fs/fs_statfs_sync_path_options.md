### `fs.statfsSync(path[, options])`

<!-- YAML
added: v19.6.0
-->

* `path` {string|Buffer|URL}
* `options` {Object}
  * `bigint` {boolean} Whether the numeric values in the returned
    {fs.StatFs} object should be `bigint`. **Default:** `false`.
* Returns: {fs.StatFs}

Synchronous statfs(2). Returns information about the mounted file system which
contains `path`.

In case of an error, the `err.code` will be one of [Common System Errors][].
