### Event: `'test:pass'`

* `data` {Object}
  * `details` {Object} Additional execution metadata.
    * `duration` {number} The duration of the test in milliseconds.
  * `file` {string|undefined} The path of the test file,
    undefined if test is not ran through a file.
  * `name` {string} The test name.
  * `nesting` {number} The nesting level of the test.
  * `testNumber` {number} The ordinal number of the test.
  * `todo` {string|boolean|undefined} Present if [`context.todo`][] is called
  * `skip` {string|boolean|undefined} Present if [`context.skip`][] is called

Emitted when a test passes.
