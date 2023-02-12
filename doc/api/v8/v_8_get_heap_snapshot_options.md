## `v8.getHeapSnapshot([options])`

<!-- YAML
added: v11.13.0
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

* Returns: {stream.Readable} A Readable containing the V8 heap snapshot.

Generates a snapshot of the current V8 heap and returns a Readable
Stream that may be used to read the JSON serialized representation.
This JSON stream format is intended to be used with tools such as
Chrome DevTools. The JSON schema is undocumented and specific to the
V8 engine. Therefore, the schema may change from one version of V8 to the next.

Creating a heap snapshot requires memory about twice the size of the heap at
the time the snapshot is created. This results in the risk of OOM killers
terminating the process.

Generating a snapshot is a synchronous operation which blocks the event loop
for a duration depending on the heap size.

```js
// Print heap snapshot to the console
const v8 = require('node:v8');
const stream = v8.getHeapSnapshot();
stream.pipe(process.stdout);
```
