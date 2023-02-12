### `fs.fdatasyncSync(fd)`

<!-- YAML
added: v0.1.96
-->

* `fd` {integer}

Forces all currently queued I/O operations associated with the file to the
operating system's synchronized I/O completion state. Refer to the POSIX
fdatasync(2) documentation for details. Returns `undefined`.
