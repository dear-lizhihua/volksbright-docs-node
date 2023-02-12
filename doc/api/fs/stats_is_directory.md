#### `stats.isDirectory()`

<!-- YAML
added: v0.1.10
-->

* Returns: {boolean}

Returns `true` if the {fs.Stats} object describes a file system directory.

If the {fs.Stats} object was obtained from [`fs.lstat()`][], this method will
always return `false`. This is because [`fs.lstat()`][] returns information
about a symbolic link itself and not the path it resolves to.
