### Event: `'message'`

<!-- YAML
added: v10.5.0
-->

* `value` {any} The transmitted value

The `'message'` event is emitted when the worker thread has invoked
[`require('node:worker_threads').parentPort.postMessage()`][].
See the [`port.on('message')`][] event for more details.

All messages sent from the worker thread are emitted before the
[`'exit'` event][] is emitted on the `Worker` object.
