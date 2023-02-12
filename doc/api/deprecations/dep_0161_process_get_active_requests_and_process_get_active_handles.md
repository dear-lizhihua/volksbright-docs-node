### DEP0161: `process._getActiveRequests()` and `process._getActiveHandles()`

<!-- YAML
changes:
  - version:
    - v17.6.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41587
    description: Documentation-only deprecation.
-->

Type: Documentation-only

The `process._getActiveHandles()` and `process._getActiveRequests()`
functions are not intended for public use and can be removed in future
releases.

Use [`process.getActiveResourcesInfo()`][] to get a list of types of active
resources and not the actual references.
