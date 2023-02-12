### Static method: `AsyncResource.bind(fn[, type[, thisArg]])`

<!-- YAML
added:
  - v14.8.0
  - v12.19.0
changes:
  - version: REPLACEME
    pr-url: https://github.com/nodejs/node/pull/46432
    description: The `asyncResource` property added to the bound function
                 has been deprecated and will be removed in a future
                 version.
  - version:
    - v17.8.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/42177
    description: Changed the default when `thisArg` is undefined to use `this`
                 from the caller.
  - version: v16.0.0
    pr-url: https://github.com/nodejs/node/pull/36782
    description: Added optional thisArg.
-->

* `fn` {Function} The function to bind to the current execution context.
* `type` {string} An optional name to associate with the underlying
  `AsyncResource`.
* `thisArg` {any}

Binds the given function to the current execution context.
