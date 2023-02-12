### `fs.fchownSync(fd, uid, gid)`

<!-- YAML
added: v0.4.7
-->

* `fd` {integer}
* `uid` {integer} The file's new owner's user id.
* `gid` {integer} The file's new group's group id.

Sets the owner of the file. Returns `undefined`.

See the POSIX fchown(2) documentation for more detail.
