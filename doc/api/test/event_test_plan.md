### Event: `'test:plan'`

* `data` {Object}
  * `file` {string|undefined} The path of the test file,
    undefined if test is not ran through a file.
  * `nesting` {number} The nesting level of the test.
  * `count` {number} The number of subtests that have ran.

Emitted when all subtests have completed for a given test.
