#### `init(promise, parent)`

* `promise` {Promise} The promise being created.
* `parent` {Promise} The promise continued from, if applicable.

Called when a promise is constructed. This _does not_ mean that corresponding
`before`/`after` events will occur, only that the possibility exists. This will
happen if a promise is created without ever getting a continuation.
