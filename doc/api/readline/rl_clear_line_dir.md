#### `rl.clearLine(dir)`

<!-- YAML
added: v17.0.0
-->

* `dir` {integer}
  * `-1`: to the left from cursor
  * `1`: to the right from cursor
  * `0`: the entire line
* Returns: this

The `rl.clearLine()` method adds to the internal list of pending action an
action that clears current line of the associated `stream` in a specified
direction identified by `dir`.
Call `rl.commit()` to see the effect of this method, unless `autoCommit: true`
was passed to the constructor.
