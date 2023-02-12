### Implementing a readable stream

The `stream.Readable` class is extended to implement a [`Readable`][] stream.

Custom `Readable` streams _must_ call the `new stream.Readable([options])`
constructor and implement the [`readable._read()`][] method.
