### DEP0150: Changing the value of `process.config`

<!-- YAML
changes:
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/43627
    description: End-of-Life.
  - version: v16.0.0
    pr-url: https://github.com/nodejs/node/pull/36902
    description: Runtime deprecation.
-->

Type: End-of-Life

The `process.config` property provides access to Node.js compile-time settings.
However, the property is mutable and therefore subject to tampering. The ability
to change the value will be removed in a future version of Node.js.
