### DEP0132: `worker.terminate()` with callback

<!-- YAML
changes:
  - version: v12.5.0
    pr-url: https://github.com/nodejs/node/pull/28021
    description: Runtime deprecation.
-->

Type: Runtime

Passing a callback to [`worker.terminate()`][] is deprecated. Use the returned
`Promise` instead, or a listener to the worker's `'exit'` event.
