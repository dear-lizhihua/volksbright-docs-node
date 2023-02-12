#### `filehandle.sync()`

<!-- YAML
added: v10.0.0
-->

* Returns: {Promise} Fulfills with `undefined` upon success.

Request that all data for the open file descriptor is flushed to the storage
device. The specific implementation is operating system and device specific.
Refer to the POSIX fsync(2) documentation for more detail.
