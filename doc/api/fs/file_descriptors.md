#### File descriptors

1. Any specified file descriptor has to support reading.
2. If a file descriptor is specified as the `path`, it will not be closed
   automatically.
3. The reading will begin at the current position. For example, if the file
   already had `'Hello World`' and six bytes are read with the file descriptor,
   the call to `fs.readFile()` with the same file descriptor, would give
   `'World'`, rather than `'Hello World'`.
