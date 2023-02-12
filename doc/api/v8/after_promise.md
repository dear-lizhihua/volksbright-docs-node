#### `after(promise)`

* `promise` {Promise}

Called immediately after a promise continuation executes. This may be after a
`then()`, `catch()`, or `finally()` handler or before an `await` after another
`await`.
