##### `writable.writable`

<!-- YAML
added: v11.4.0
-->

* {boolean}

Is `true` if it is safe to call [`writable.write()`][stream-write], which means
the stream has not been destroyed, errored, or ended.
