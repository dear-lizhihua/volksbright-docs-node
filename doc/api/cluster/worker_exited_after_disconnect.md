### `worker.exitedAfterDisconnect`

<!-- YAML
added: v6.0.0
-->

* {boolean}

This property is `true` if the worker exited due to `.disconnect()`.
If the worker exited any other way, it is `false`. If the
worker has not exited, it is `undefined`.

The boolean [`worker.exitedAfterDisconnect`][] allows distinguishing between
voluntary and accidental exit, the primary may choose not to respawn a worker
based on this value.

```js
cluster.on('exit', (worker, code, signal) => {
  if (worker.exitedAfterDisconnect === true) {
    console.log('Oh, it was just voluntary – no need to worry');
  }
});

// kill worker
worker.kill();
```
