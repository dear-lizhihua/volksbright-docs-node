## `v8.setHeapSnapshotNearHeapLimit(limit)`

<!-- YAML
added:
  - v18.10.0
  - v16.18.0
-->

> Stability: 1 - Experimental

* `limit` {integer}

The API is a no-op if `--heapsnapshot-near-heap-limit` is already set from the
command line or the API is called more than once. `limit` must be a positive
integer. See [`--heapsnapshot-near-heap-limit`][] for more information.
