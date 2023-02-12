### `fs.chmodSync(path, mode)`

<!-- YAML
added: v0.6.7
changes:
  - version: v7.6.0
    pr-url: https://github.com/nodejs/node/pull/10739
    description: The `path` parameter can be a WHATWG `URL` object using `file:`
                 protocol.
-->

* `path` {string|Buffer|URL}
* `mode` {string|integer}

For detailed information, see the documentation of the asynchronous version of
this API: [`fs.chmod()`][].

See the POSIX chmod(2) documentation for more detail.
