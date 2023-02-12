#### `resolve(specifier, context, nextResolve)`

<!-- YAML
changes:
  - version:
    - v18.6.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42623
    description: Add support for chaining resolve hooks. Each hook must either
      call `nextResolve()` or include a `shortCircuit` property set to `true`
      in its return.
  - version:
    - v17.1.0
    - v16.14.0
    pr-url: https://github.com/nodejs/node/pull/40250
    description: Add support for import assertions.
-->

> The loaders API is being redesigned. This hook may disappear or its
> signature may change. Do not rely on the API described below.

* `specifier` {string}
* `context` {Object}
  * `conditions` {string\[]} Export conditions of the relevant `package.json`
  * `importAssertions` {Object} An object whose key-value pairs represent the
    assertions for the module to import
  * `parentURL` {string|undefined} The module importing this one, or undefined
    if this is the Node.js entry point
* `nextResolve` {Function} The subsequent `resolve` hook in the chain, or the
  Node.js default `resolve` hook after the last user-supplied `resolve` hook
  * `specifier` {string}
  * `context` {Object}
* Returns: {Object}
  * `format` {string|null|undefined} A hint to the load hook (it might be
    ignored)
    `'builtin' | 'commonjs' | 'json' | 'module' | 'wasm'`
  * `importAssertions` {Object|undefined} The import assertions to use when
    caching the module (optional; if excluded the input will be used)
  * `shortCircuit` {undefined|boolean} A signal that this hook intends to
    terminate the chain of `resolve` hooks. **Default:** `false`
  * `url` {string} The absolute URL to which this input resolves

The `resolve` hook chain is responsible for telling Node.js where to find and
how to cache a given `import` statement or expression. It can optionally return
its format (such as `'module'`) as a hint to the `load` hook. If a format is
specified, the `load` hook is ultimately responsible for providing the final
`format` value (and it is free to ignore the hint provided by `resolve`); if
`resolve` provides a `format`, a custom `load` hook is required even if only to
pass the value to the Node.js default `load` hook.

Import type assertions are part of the cache key for saving loaded modules into
the internal module cache. The `resolve` hook is responsible for
returning an `importAssertions` object if the module should be cached with
different assertions than were present in the source code.

The `conditions` property in `context` is an array of conditions for
[package exports conditions][Conditional Exports] that apply to this resolution
request. They can be used for looking up conditional mappings elsewhere or to
modify the list when calling the default resolution logic.

The current [package exports conditions][Conditional Exports] are always in
the `context.conditions` array passed into the hook. To guarantee _default
Node.js module specifier resolution behavior_ when calling `defaultResolve`, the
`context.conditions` array passed to it _must_ include _all_ elements of the
`context.conditions` array originally passed into the `resolve` hook.

```js
export async function resolve(specifier, context, nextResolve) {
  const { parentURL = null } = context;

  if (Math.random() > 0.5) { // Some condition.
    // For some or all specifiers, do some custom logic for resolving.
    // Always return an object of the form {url: <string>}.
    return {
      shortCircuit: true,
      url: parentURL ?
        new URL(specifier, parentURL).href :
        new URL(specifier).href,
    };
  }

  if (Math.random() < 0.5) { // Another condition.
    // When calling `defaultResolve`, the arguments can be modified. In this
    // case it's adding another value for matching conditional exports.
    return nextResolve(specifier, {
      ...context,
      conditions: [...context.conditions, 'another-condition'],
    });
  }

  // Defer to the next hook in the chain, which would be the
  // Node.js default resolve if this is the last user-specified loader.
  return nextResolve(specifier);
}
```
