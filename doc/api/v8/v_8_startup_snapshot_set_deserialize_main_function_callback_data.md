### `v8.startupSnapshot.setDeserializeMainFunction(callback[, data])`

<!-- YAML
added:
  - v18.6.0
  - v16.17.0
-->

* `callback` {Function} Callback to be invoked as the entry point after the
  snapshot is deserialized.
* `data` {any} Optional data that will be passed to the `callback` when it
  gets called.

This sets the entry point of the Node.js application when it is deserialized
from a snapshot. This can be called only once in the snapshot building
script. If called, the deserialized application no longer needs an additional
entry point script to start up and will simply invoke the callback along with
the deserialized data (if provided), otherwise an entry point script still
needs to be provided to the deserialized application.
