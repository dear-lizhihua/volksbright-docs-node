### `v8.startupSnapshot.addDeserializeCallback(callback[, data])`

<!-- YAML
added:
  - v18.6.0
  - v16.17.0
-->

* `callback` {Function} Callback to be invoked after the snapshot is
  deserialized.
* `data` {any} Optional data that will be passed to the `callback` when it
  gets called.

Add a callback that will be called when the Node.js instance is deserialized
from a snapshot. The `callback` and the `data` (if provided) will be
serialized into the snapshot, they can be used to re-initialize the state
of the application or to re-acquire resources that the application needs
when the application is restarted from the snapshot.
