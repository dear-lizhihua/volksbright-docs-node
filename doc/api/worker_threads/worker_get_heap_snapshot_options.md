### `worker.getHeapSnapshot([options])`

<!-- YAML
added:
 - v13.9.0
 - v12.17.0
changes:
  - version: v19.1.0
    pr-url: https://github.com/nodejs/node/pull/44989
    description: Support options to configure the heap snapshot.
-->

* `options` {Object}
  * `exposeInternals` {boolean} If true, expose internals in the heap snapshot.
    **Default:** `false`.
  * `exposeNumericValues` {boolean} If true, expose numeric values in
    artificial fields. **Default:** `false`.
* Returns: {Promise} A promise for a Readable Stream containing
  a V8 heap snapshot

Returns a readable stream for a V8 snapshot of the current state of the Worker.
See [`v8.getHeapSnapshot()`][] for more details.

If the Worker thread is no longer running, which may occur before the
[`'exit'` event][] is emitted, the returned `Promise` is rejected
immediately with an [`ERR_WORKER_NOT_RUNNING`][] error.
