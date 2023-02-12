### DEP0136: `http` `finished`

<!-- YAML
changes:
  - version:
     - v13.4.0
     - v12.16.0
    pr-url: https://github.com/nodejs/node/pull/28679
    description: Documentation-only deprecation.
-->

Type: Documentation-only

[`response.finished`][] indicates whether [`response.end()`][] has been
called, not whether `'finish'` has been emitted and the underlying data
is flushed.

Use [`response.writableFinished`][] or [`response.writableEnded`][]
accordingly instead to avoid the ambiguity.

To maintain existing behavior `response.finished` should be replaced with
`response.writableEnded`.
