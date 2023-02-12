### Event: `'test:start'`

* `data` {Object}
  * `file` {string|undefined} The path of the test file,
    undefined if test is not ran through a file.
  * `name` {string} The test name.
  * `nesting` {number} The nesting level of the test.

Emitted when a test starts.
