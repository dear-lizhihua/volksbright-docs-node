### Event: `'error'`

* `err` {Error} The error.

The `'error'` event is emitted whenever:

* The process could not be spawned.
* The process could not be killed.
* Sending a message to the child process failed.
* The child process was aborted via the `signal` option.

The `'exit'` event may or may not fire after an error has occurred. When
listening to both the `'exit'` and `'error'` events, guard
against accidentally invoking handler functions multiple times.

See also [`subprocess.kill()`][] and [`subprocess.send()`][].
