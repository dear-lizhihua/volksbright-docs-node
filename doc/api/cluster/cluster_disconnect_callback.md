## `cluster.disconnect([callback])`

<!-- YAML
added: v0.7.7
-->

* `callback` {Function} Called when all workers are disconnected and handles are
  closed.

Calls `.disconnect()` on each worker in `cluster.workers`.

When they are disconnected all internal handles will be closed, allowing the
primary process to die gracefully if no other event is waiting.

The method takes an optional callback argument which will be called when
finished.

This can only be called from the primary process.
