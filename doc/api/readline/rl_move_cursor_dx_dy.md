#### `rl.moveCursor(dx, dy)`

<!-- YAML
added: v17.0.0
-->

* `dx` {integer}
* `dy` {integer}
* Returns: this

The `rl.moveCursor()` method adds to the internal list of pending action an
action that moves the cursor _relative_ to its current position in the
associated `stream`.
Call `rl.commit()` to see the effect of this method, unless `autoCommit: true`
was passed to the constructor.
