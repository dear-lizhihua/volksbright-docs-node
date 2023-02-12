### DEP0164: `process.exit(code)`, `process.exitCode` coercion to integer

<!-- YAML
changes:
  - version: REPLACEME
    pr-url: https://github.com/nodejs/node/pull/43716
    description: End-of-Life.
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/44711
    description: Runtime deprecation.
  - version:
    - v18.10.0
    - v16.18.0
    pr-url: https://github.com/nodejs/node/pull/44714
    description: Documentation-only deprecation of `process.exitCode` integer
                 coercion.
  - version:
    - v18.7.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/43738
    description: Documentation-only deprecation of `process.exit(code)` integer
                 coercion.
-->

Type: End-of-Life

Values other than `undefined`, `null`, integer numbers, and integer strings
(e.g., `'1'`) are deprecated as value for the `code` parameter in
[`process.exit()`][] and as value to assign to [`process.exitCode`][].
