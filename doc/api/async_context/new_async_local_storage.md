### `new AsyncLocalStorage()`

<!-- YAML
added:
 - v13.10.0
 - v12.17.0
changes:
 - version: REPLACEME
   pr-url: https://github.com/nodejs/node/pull/46386
   description: Removed experimental onPropagate option.
 - version:
    - v19.2.0
    - v18.13.0
   pr-url: https://github.com/nodejs/node/pull/45386
   description: Add option onPropagate.
-->

Creates a new instance of `AsyncLocalStorage`. Store is only provided within a
`run()` call or after an `enterWith()` call.
