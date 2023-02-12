### DEP0162: `fs.write()`, `fs.writeFileSync()` coercion to string

<!-- YAML
changes:
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/42796
    description: End-of-Life.
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/42607
    description: Runtime deprecation.
  - version:
    - v17.8.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/42149
    description: Documentation-only deprecation.
-->

Type: End-of-Life

Implicit coercion of objects with own `toString` property, passed as second
parameter in [`fs.write()`][], [`fs.writeFile()`][], [`fs.appendFile()`][],
[`fs.writeFileSync()`][], and [`fs.appendFileSync()`][] is deprecated.
Convert them to primitive strings.
