#### `rl.cursorTo(x[, y])`

<!-- YAML
added: v17.0.0
-->

* `x` {integer}
* `y` {integer}
* Returns: this

The `rl.cursorTo()` method adds to the internal list of pending action an action
that moves cursor to the specified position in the associated `stream`.
Call `rl.commit()` to see the effect of this method, unless `autoCommit: true`
was passed to the constructor.
