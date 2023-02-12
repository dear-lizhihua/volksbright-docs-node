### `fs.lchownSync(path, uid, gid)`

<!-- YAML
changes:
  - version: v10.6.0
    pr-url: https://github.com/nodejs/node/pull/21498
    description: This API is no longer deprecated.
  - version: v0.4.7
    description: Documentation-only deprecation.
-->

* `path` {string|Buffer|URL}
* `uid` {integer} The file's new owner's user id.
* `gid` {integer} The file's new group's group id.

Set the owner for the path. Returns `undefined`.

See the POSIX lchown(2) documentation for more details.
