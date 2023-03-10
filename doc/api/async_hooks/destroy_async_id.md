#### `destroy(asyncId)`

* `asyncId` {number}

Called after the resource corresponding to `asyncId` is destroyed. It is also
called asynchronously from the embedder API `emitDestroy()`.

Some resources depend on garbage collection for cleanup, so if a reference is
made to the `resource` object passed to `init` it is possible that `destroy`
will never be called, causing a memory leak in the application. If the resource
does not depend on garbage collection, then this will not be an issue.

Using the destroy hook results in additional overhead because it enables
tracking of `Promise` instances via the garbage collector.
