### DEP0158: `buffer.slice(start, end)`

<!-- YAML
changes:
  - version:
    - v17.5.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41596
    description: Documentation-only deprecation.
-->

Type: Documentation-only

This method was deprecated because it is not compatible with
`Uint8Array.prototype.slice()`, which is a superclass of `Buffer`.

Use [`buffer.subarray`][] which does the same thing instead.
