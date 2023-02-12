## `it([name][, options][, fn])`

* `name` {string} The name of the test, which is displayed when reporting test
  results. **Default:** The `name` property of `fn`, or `'<anonymous>'` if `fn`
  does not have a name.
* `options` {Object} Configuration options for the suite.
  supports the same options as `test([name][, options][, fn])`.
* `fn` {Function|AsyncFunction} The function under test.
  If the test uses callbacks, the callback function is passed as an argument.
  **Default:** A no-op function.
* Returns: `undefined`.

The `it()` function is the value imported from the `node:test` module.
