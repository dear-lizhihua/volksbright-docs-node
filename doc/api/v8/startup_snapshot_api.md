## Startup Snapshot API

<!-- YAML
added:
  - v18.6.0
  - v16.17.0
-->

> Stability: 1 - Experimental

The `v8.startupSnapshot` interface can be used to add serialization and
deserialization hooks for custom startup snapshots. Currently the startup
snapshots can only be built into the Node.js binary from source.

```console
$ cd /path/to/node
$ ./configure --node-snapshot-main=entry.js
$ make node