##### `readable.readable`

<!-- YAML
added: v11.4.0
-->

* {boolean}

Is `true` if it is safe to call [`readable.read()`][stream-read], which means
the stream has not been destroyed or emitted `'error'` or `'end'`.
