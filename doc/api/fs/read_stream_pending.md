#### `readStream.pending`

<!-- YAML
added:
 - v11.2.0
 - v10.16.0
-->

* {boolean}

This property is `true` if the underlying file has not been opened yet,
i.e. before the `'ready'` event is emitted.
