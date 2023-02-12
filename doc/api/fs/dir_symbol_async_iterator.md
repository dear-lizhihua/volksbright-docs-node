#### `dir[Symbol.asyncIterator]()`

<!-- YAML
added: v12.12.0
-->

* Returns: {AsyncIterator} of {fs.Dirent}

Asynchronously iterates over the directory until all entries have
been read. Refer to the POSIX readdir(3) documentation for more detail.

Entries returned by the async iterator are always an {fs.Dirent}.
The `null` case from `dir.read()` is handled internally.

See {fs.Dir} for an example.

Directory entries returned by this iterator are in no particular order as
provided by the operating system's underlying directory mechanisms.
Entries added or removed while iterating over the directory might not be
included in the iteration results.
