## `describe([name][, options][, fn])`

* `name` {string} The name of the suite, which is displayed when reporting test
  results. **Default:** The `name` property of `fn`, or `'<anonymous>'` if `fn`
  does not have a name.
* `options` {Object} Configuration options for the suite.
  supports the same options as `test([name][, options][, fn])`.
* `fn` {Function|AsyncFunction} The function under suite
  declaring all subtests and subsuites.
  The first argument to this function is a [`SuiteContext`][] object.
  **Default:** A no-op function.
* Returns: `undefined`.

The `describe()` function imported from the `node:test` module. Each
invocation of this function results in the creation of a Subtest.
After invocation of top level `describe` functions,
all top level tests and suites will execute.
