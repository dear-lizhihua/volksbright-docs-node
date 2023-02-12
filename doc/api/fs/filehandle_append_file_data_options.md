#### `filehandle.appendFile(data[, options])`

<!-- YAML
added: v10.0.0
changes:
  - version:
      - v15.14.0
      - v14.18.0
    pr-url: https://github.com/nodejs/node/pull/37490
    description: The `data` argument supports `AsyncIterable`, `Iterable`, and `Stream`.
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/31030
    description: The `data` parameter won't coerce unsupported input to
                 strings anymore.
-->

* `data` {string|Buffer|TypedArray|DataView|AsyncIterable|Iterable|Stream}
* `options` {Object|string}
  * `encoding` {string|null} **Default:** `'utf8'`
* Returns: {Promise} Fulfills with `undefined` upon success.

Alias of [`filehandle.writeFile()`][].

When operating on file handles, the mode cannot be changed from what it was set
to with [`fsPromises.open()`][]. Therefore, this is equivalent to
[`filehandle.writeFile()`][].
