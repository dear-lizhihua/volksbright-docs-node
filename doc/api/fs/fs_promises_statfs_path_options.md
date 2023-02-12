### `fsPromises.statfs(path[, options])`

<!-- YAML
added: v19.6.0
-->

* `path` {string|Buffer|URL}
* `options` {Object}
  * `bigint` {boolean} Whether the numeric values in the returned
    {fs.StatFs} object should be `bigint`. **Default:** `false`.
* Returns: {Promise} Fulfills with the {fs.StatFs} object for the
  given `path`.
