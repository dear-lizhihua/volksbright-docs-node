### `--snapshot-blob=path`

<!-- YAML
added: v18.8.0
-->

> Stability: 1 - Experimental

When used with `--build-snapshot`, `--snapshot-blob` specifies the path
where the generated snapshot blob is written to. If not specified, the
generated blob is written to `snapshot.blob` in the current working directory.

When used without `--build-snapshot`, `--snapshot-blob` specifies the
path to the blob that is used to restore the application state.

When loading a snapshot, Node.js checks that:

1. The version, architecture and platform of the running Node.js binary
   are exactly the same as that of the binary that generates the snapshot.
2. The V8 flags and CPU features are compatible with that of the binary
   that generates the snapshot.

If they don't match, Node.js refuses to load the snapshot and exits with
status code 1.
