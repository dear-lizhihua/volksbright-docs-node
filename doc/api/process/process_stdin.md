## `process.stdin`

* {Stream}

The `process.stdin` property returns a stream connected to
`stdin` (fd `0`). It is a [`net.Socket`][] (which is a [Duplex][]
stream) unless fd `0` refers to a file, in which case it is
a [Readable][] stream.

For details of how to read from `stdin` see [`readable.read()`][].

As a [Duplex][] stream, `process.stdin` can also be used in "old" mode that
is compatible with scripts written for Node.js prior to v0.10.
For more information see [Stream compatibility][].

In "old" streams mode the `stdin` stream is paused by default, so one
must call `process.stdin.resume()` to read from it. Note also that calling
`process.stdin.resume()` itself would switch stream to "old" mode.
