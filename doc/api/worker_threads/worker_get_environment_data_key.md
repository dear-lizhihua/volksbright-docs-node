## `worker.getEnvironmentData(key)`

<!-- YAML
added:
  - v15.12.0
  - v14.18.0
changes:
  - version:
    - v17.5.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41272
    description: No longer experimental.
-->

* `key` {any} Any arbitrary, cloneable JavaScript value that can be used as a
  {Map} key.
* Returns: {any}

Within a worker thread, `worker.getEnvironmentData()` returns a clone
of data passed to the spawning thread's `worker.setEnvironmentData()`.
Every new `Worker` receives its own copy of the environment data
automatically.

```js
const {
  Worker,
  isMainThread,
  setEnvironmentData,
  getEnvironmentData,
} = require('node:worker_threads');

if (isMainThread) {
  setEnvironmentData('Hello', 'World!');
  const worker = new Worker(__filename);
} else {
  console.log(getEnvironmentData('Hello'));  // Prints 'World!'.
}
```
