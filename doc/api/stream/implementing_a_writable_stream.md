### Implementing a writable stream

The `stream.Writable` class is extended to implement a [`Writable`][] stream.

Custom `Writable` streams _must_ call the `new stream.Writable([options])`
constructor and implement the `writable._write()` and/or `writable._writev()`
method.
