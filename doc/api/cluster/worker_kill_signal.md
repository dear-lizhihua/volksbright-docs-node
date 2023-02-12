### `worker.kill([signal])`

<!-- YAML
added: v0.9.12
-->

* `signal` {string} Name of the kill signal to send to the worker
  process. **Default:** `'SIGTERM'`

This function will kill the worker. In the primary worker, it does this by
disconnecting the `worker.process`, and once disconnected, killing with
`signal`. In the worker, it does it by killing the process with `signal`.

The `kill()` function kills the worker process without waiting for a graceful
disconnect, it has the same behavior as `worker.process.kill()`.

This method is aliased as `worker.destroy()` for backwards compatibility.

In a worker, `process.kill()` exists, but it is not this function;
it is [`kill()`][].
