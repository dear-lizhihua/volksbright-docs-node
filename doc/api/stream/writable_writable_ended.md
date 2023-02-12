##### `writable.writableEnded`

<!-- YAML
added: v12.9.0
-->

* {boolean}

Is `true` after [`writable.end()`][] has been called. This property
does not indicate whether the data has been flushed, for this use
[`writable.writableFinished`][] instead.
