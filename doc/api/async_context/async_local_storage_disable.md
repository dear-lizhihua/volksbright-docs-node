### `asyncLocalStorage.disable()`

<!-- YAML
added:
 - v13.10.0
 - v12.17.0
-->

> Stability: 1 - Experimental

Disables the instance of `AsyncLocalStorage`. All subsequent calls
to `asyncLocalStorage.getStore()` will return `undefined` until
`asyncLocalStorage.run()` or `asyncLocalStorage.enterWith()` is called again.

When calling `asyncLocalStorage.disable()`, all current contexts linked to the
instance will be exited.

Calling `asyncLocalStorage.disable()` is required before the
`asyncLocalStorage` can be garbage collected. This does not apply to stores
provided by the `asyncLocalStorage`, as those objects are garbage collected
along with the corresponding async resources.

Use this method when the `asyncLocalStorage` is not in use anymore
in the current process.
