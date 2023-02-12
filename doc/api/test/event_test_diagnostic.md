### Event: `'test:diagnostic'`

* `data` {Object}
  * `file` {string|undefined} The path of the test file,
    undefined if test is not ran through a file.
  * `message` {string} The diagnostic message.
  * `nesting` {number} The nesting level of the test.

Emitted when [`context.diagnostic`][] is called.
