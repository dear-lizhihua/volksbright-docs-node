### `fs.statfs(path[, options], callback)`

<!-- YAML
added: v19.6.0
-->

* `path` {string|Buffer|URL}
* `options` {Object}
  * `bigint` {boolean} Whether the numeric values in the returned
    {fs.StatFs} object should be `bigint`. **Default:** `false`.
* `callback` {Function}
  * `err` {Error}
  * `stats` {fs.StatFs}

Asynchronous statfs(2). Returns information about the mounted file system which
contains `path`. The callback gets two arguments `(err, stats)` where `stats`
is an {fs.StatFs} object.

In case of an error, the `err.code` will be one of [Common System Errors][].
