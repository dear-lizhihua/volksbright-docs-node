### `v8.startupSnapshot.addSerializeCallback(callback[, data])`

<!-- YAML
added:
  - v18.6.0
  - v16.17.0
-->

* `callback` {Function} Callback to be invoked before serialization.
* `data` {any} Optional data that will be passed to the `callback` when it
  gets called.

Add a callback that will be called when the Node.js instance is about to
get serialized into a snapshot and exit. This can be used to release
resources that should not or cannot be serialized or to convert user data
into a form more suitable for serialization.
