### `worker.postMessage(value[, transferList])`

<!-- YAML
added: v10.5.0
-->

* `value` {any}
* `transferList` {Object\[]}

Send a message to the worker that is received via
[`require('node:worker_threads').parentPort.on('message')`][].
See [`port.postMessage()`][] for more details.
