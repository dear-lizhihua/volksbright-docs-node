### DEP0152: Extension PerformanceEntry properties

<!-- YAML
changes:
  - version: v16.0.0
    pr-url: https://github.com/nodejs/node/pull/37136
    description: Runtime deprecation.
-->

Type: Runtime

The `'gc'`, `'http2'`, and `'http'` {PerformanceEntry} object types have
additional properties assigned to them that provide additional information.
These properties are now available within the standard `detail` property
of the `PerformanceEntry` object. The existing accessors have been
deprecated and should no longer be used.
