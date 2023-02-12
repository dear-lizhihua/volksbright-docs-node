### Threadpool usage

All callback and promise-based file system APIs (with the exception of
`fs.FSWatcher()`) use libuv's threadpool. This can have surprising and negative
performance implications for some applications. See the
[`UV_THREADPOOL_SIZE`][] documentation for more information.
