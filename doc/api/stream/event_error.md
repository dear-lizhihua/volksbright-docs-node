##### Event: `'error'`

<!-- YAML
added: v0.9.4
-->

* {Error}

The `'error'` event is emitted if an error occurred while writing or piping
data. The listener callback is passed a single `Error` argument when called.

The stream is closed when the `'error'` event is emitted unless the
[`autoDestroy`][writable-new] option was set to `false` when creating the
stream.

After `'error'`, no further events other than `'close'` _should_ be emitted
(including `'error'` events).
