#### `server.listen(path[, backlog][, callback])`

<!-- YAML
added: v0.1.90
-->

* `path` {string} Path the server should listen to. See
  [Identifying paths for IPC connections][].
* `backlog` {number} Common parameter of [`server.listen()`][] functions.
* `callback` {Function}.
* Returns: {net.Server}

Start an [IPC][] server listening for connections on the given `path`.
