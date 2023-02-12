### `fs.fsyncSync(fd)`

<!-- YAML
added: v0.1.96
-->

* `fd` {integer}

Request that all data for the open file descriptor is flushed to the storage
device. The specific implementation is operating system and device specific.
Refer to the POSIX fsync(2) documentation for more detail. Returns `undefined`.
