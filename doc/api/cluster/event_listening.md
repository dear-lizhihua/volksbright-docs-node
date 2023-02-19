### Event: `'listening'`

<!-- YAML
added: v0.7.0
-->

* `address` {Object}

Similar to the `cluster.on('listening')` event, but specific to this worker.

```mjs
cluster.fork().on('listening', (address) => {
  // Worker is listening
});
```

```cjs
cluster.fork().on('listening', (address) => {
  // Worker is listening
});
```

It is not emitted in the worker.
