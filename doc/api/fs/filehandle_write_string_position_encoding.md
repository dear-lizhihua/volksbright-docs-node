#### `filehandle.write(string[, position[, encoding]])`

<!-- YAML
added: v10.0.0
changes:
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/31030
    description: The `string` parameter won't coerce unsupported input to
                 strings anymore.
-->

* `string` {string}
* `position` {integer|null} The offset from the beginning of the file where the
  data from `string` should be written. If `position` is not a `number` the
  data will be written at the current position. See the POSIX pwrite(2)
  documentation for more detail. **Default:** `null`
* `encoding` {string} The expected string encoding. **Default:** `'utf8'`
* Returns: {Promise}

Write `string` to the file. If `string` is not a string, the promise is
rejected with an error.

The promise is resolved with an object containing two properties:

* `bytesWritten` {integer} the number of bytes written
* `buffer` {string} a reference to the `string` written.

It is unsafe to use `filehandle.write()` multiple times on the same file
without waiting for the promise to be resolved (or rejected). For this
scenario, use [`filehandle.createWriteStream()`][].

On Linux, positional writes do not work when the file is opened in append mode.
The kernel ignores the position argument and always appends the data to
the end of the file.
