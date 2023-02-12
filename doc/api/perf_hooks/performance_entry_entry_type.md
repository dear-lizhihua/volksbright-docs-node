### `performanceEntry.entryType`

<!-- YAML
added: v8.5.0
changes:
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/44483
    description: This property getter must be called with the
                 `PerformanceEntry` object as the receiver.
-->

* {string}

The type of the performance entry. It may be one of:

* `'node'` (Node.js only)
* `'mark'` (available on the Web)
* `'measure'` (available on the Web)
* `'gc'` (Node.js only)
* `'function'` (Node.js only)
* `'http2'` (Node.js only)
* `'http'` (Node.js only)
