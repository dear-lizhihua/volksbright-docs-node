## `cluster.fork([env])`

<!-- YAML
added: v0.6.0
-->

* `env` {Object} Key/value pairs to add to worker process environment.
* Returns: {cluster.Worker}

Spawn a new worker process.

This can only be called from the primary process.
