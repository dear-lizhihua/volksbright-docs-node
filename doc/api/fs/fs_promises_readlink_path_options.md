### `fsPromises.readlink(path[, options])`

<!-- YAML
added: v10.0.0
-->

* `path` {string|Buffer|URL}
* `options` {string|Object}
  * `encoding` {string} **Default:** `'utf8'`
* Returns: {Promise} Fulfills with the `linkString` upon success.

Reads the contents of the symbolic link referred to by `path`. See the POSIX
readlink(2) documentation for more detail. The promise is resolved with the
`linkString` upon success.

The optional `options` argument can be a string specifying an encoding, or an
object with an `encoding` property specifying the character encoding to use for
the link path returned. If the `encoding` is set to `'buffer'`, the link path
returned will be passed as a {Buffer} object.
