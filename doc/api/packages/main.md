### `"main"`

<!-- YAML
added: v0.4.0
-->

* Type: {string}

```json
{
  "main": "./index.js"
}
```

The `"main"` field defines the entry point of a package when imported by name
via a `node_modules` lookup.  Its value is a path.

When a package has an [`"exports"`][] field, this will take precedence over the
`"main"` field when importing the package by name.

It also defines the script that is used when the [package directory is loaded
via `require()`](modules.md#folders-as-modules).

```cjs
// This resolves to ./path/to/directory/index.js.
require('./path/to/directory');
```
