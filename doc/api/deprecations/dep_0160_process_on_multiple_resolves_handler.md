### DEP0160: `process.on('multipleResolves', handler)`

<!-- YAML
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41896
    description: Runtime deprecation.
  - version:
    - v17.6.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41872
    description: Documentation-only deprecation.
-->

Type: Runtime.

This event was deprecated because it did not work with V8 promise combinators
which diminished its usefulness.
