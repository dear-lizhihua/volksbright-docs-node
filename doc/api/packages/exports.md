### `"exports"`

<!-- YAML
added: v12.7.0
changes:
  - version:
    - v14.13.0
    - v12.20.0
    pr-url: https://github.com/nodejs/node/pull/34718
    description: Add support for `"exports"` patterns.
  - version:
    - v13.7.0
    - v12.17.0
    pr-url: https://github.com/nodejs/node/pull/29866
    description: Unflag conditional exports.
  - version:
    - v13.7.0
    - v12.16.0
    pr-url: https://github.com/nodejs/node/pull/31008
    description: Implement logical conditional exports ordering.
  - version:
    - v13.7.0
    - v12.16.0
    pr-url: https://github.com/nodejs/node/pull/31001
    description: Remove the `--experimental-conditional-exports` option. In 12.16.0, conditional exports are still behind `--experimental-modules`.
  - version:
    - v13.2.0
    - v12.16.0
    pr-url: https://github.com/nodejs/node/pull/29978
    description: Implement conditional exports.
-->

* Type: {Object} | {string} | {string\[]}

```json
{
  "exports": "./index.js"
}
```

The `"exports"` field allows defining the [entry points][] of a package when
imported by name loaded either via a `node_modules` lookup or a
[self-reference][] to its own name. It is supported in Node.js 12+ as an
alternative to the [`"main"`][] that can support defining [subpath exports][]
and [conditional exports][] while encapsulating internal unexported modules.

[Conditional Exports][] can also be used within `"exports"` to define different
package entry points per environment, including whether the package is
referenced via `require` or via `import`.

All paths defined in the `"exports"` must be relative file URLs starting with
`./`.
