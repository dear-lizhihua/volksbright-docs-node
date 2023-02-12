### `fsPromises.appendFile(path, data[, options])`

<!-- YAML
added: v10.0.0
-->

* `path` {string|Buffer|URL|FileHandle} filename or {FileHandle}
* `data` {string|Buffer}
* `options` {Object|string}
  * `encoding` {string|null} **Default:** `'utf8'`
  * `mode` {integer} **Default:** `0o666`
  * `flag` {string} See [support of file system `flags`][]. **Default:** `'a'`.
* Returns: {Promise} Fulfills with `undefined` upon success.

Asynchronously append data to a file, creating the file if it does not yet
exist. `data` can be a string or a {Buffer}.

If `options` is a string, then it specifies the `encoding`.

The `mode` option only affects the newly created file. See [`fs.open()`][]
for more details.

The `path` may be specified as a {FileHandle} that has been opened
for appending (using `fsPromises.open()`).
