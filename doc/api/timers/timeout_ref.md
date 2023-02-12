### `timeout.ref()`

<!-- YAML
added: v0.9.1
-->

* Returns: {Timeout} a reference to `timeout`

When called, requests that the Node.js event loop _not_ exit so long as the
`Timeout` is active. Calling `timeout.ref()` multiple times will have no effect.

By default, all `Timeout` objects are "ref'ed", making it normally unnecessary
to call `timeout.ref()` unless `timeout.unref()` had been called previously.
