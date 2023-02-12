#### `after(asyncId)`

* `asyncId` {number}

Called immediately after the callback specified in `before` is completed.

If an uncaught exception occurs during execution of the callback, then `after`
will run _after_ the `'uncaughtException'` event is emitted or a `domain`'s
handler runs.
