## `process.disconnect()`

<!-- YAML
added: v0.7.2
-->

If the Node.js process is spawned with an IPC channel (see the [Child Process][]
and [Cluster][] documentation), the `process.disconnect()` method will close the
IPC channel to the parent process, allowing the child process to exit gracefully
once there are no other connections keeping it alive.

The effect of calling `process.disconnect()` is the same as calling
[`ChildProcess.disconnect()`][] from the parent process.

If the Node.js process was not spawned with an IPC channel,
`process.disconnect()` will be `undefined`.
