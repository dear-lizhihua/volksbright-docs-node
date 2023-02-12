### DEP0168: Unhandled exception in Node-API callbacks

<!-- YAML
changes:
  - version:
    - v18.3.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/36510
    description: Runtime deprecation.
-->

Type: Runtime

The implicit suppression of uncaught exceptions in Node-API callbacks is now
deprecated.

Set the flag [`--force-node-api-uncaught-exceptions-policy`][] to force Node.js
to emit an [`'uncaughtException'`][] event if the exception is not handled in
Node-API callbacks.
