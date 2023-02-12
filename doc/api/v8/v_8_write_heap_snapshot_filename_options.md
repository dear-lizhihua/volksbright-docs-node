## `v8.writeHeapSnapshot([filename[,options]])`

<!-- YAML
added: v11.13.0
changes:
  - version: v19.1.0
    pr-url: https://github.com/nodejs/node/pull/44989
    description: Support options to configure the heap snapshot.
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41373
    description: An exception will now be thrown if the file could not be written.
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/42577
    description: Make the returned error codes consistent across all platforms.
-->

* `filename` {string} The file path where the V8 heap snapshot is to be
  saved. If not specified, a file name with the pattern
  `'Heap-${yyyymmdd}-${hhmmss}-${pid}-${thread_id}.heapsnapshot'` will be
  generated, where `{pid}` will be the PID of the Node.js process,
  `{thread_id}` will be `0` when `writeHeapSnapshot()` is called from
  the main Node.js thread or the id of a worker thread.
* `options` {Object}
  * `exposeInternals` {boolean} If true, expose internals in the heap snapshot.
    **Default:** `false`.
  * `exposeNumericValues` {boolean} If true, expose numeric values in
    artificial fields. **Default:** `false`.
* Returns: {string} The filename where the snapshot was saved.

Generates a snapshot of the current V8 heap and writes it to a JSON
file. This file is intended to be used with tools such as Chrome
DevTools. The JSON schema is undocumented and specific to the V8
engine, and may change from one version of V8 to the next.

A heap snapshot is specific to a single V8 isolate. When using
[worker threads][], a heap snapshot generated from the main thread will
not contain any information about the workers, and vice versa.

Creating a heap snapshot requires memory about twice the size of the heap at
the time the snapshot is created. This results in the risk of OOM killers
terminating the process.

Generating a snapshot is a synchronous operation which blocks the event loop
for a duration depending on the heap size.

```js
const { writeHeapSnapshot } = require('node:v8');
const {
  Worker,
  isMainThread,
  parentPort,
} = require('node:worker_threads');

if (isMainThread) {
  const worker = new Worker(__filename);

  worker.once('message', (filename) => {
    console.log(`worker heapdump: ${filename}`);
    // Now get a heapdump for the main thread.
    console.log(`main thread heapdump: ${writeHeapSnapshot()}`);
  });

  // Tell the worker to create a heapdump.
  worker.postMessage('heapdump');
} else {
  parentPort.once('message', (message) => {
    if (message === 'heapdump') {
      // Generate a heapdump for the worker
      // and return the filename to the parent.
      parentPort.postMessage(writeHeapSnapshot());
    }
  });
}
```
