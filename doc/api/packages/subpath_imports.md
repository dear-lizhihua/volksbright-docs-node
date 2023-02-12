### Subpath imports

<!-- YAML
added:
  - v14.6.0
  - v12.19.0
-->

In addition to the [`"exports"`][] field, there is a package `"imports"` field
to create private mappings that only apply to import specifiers from within the
package itself.

Entries in the `"imports"` field must always start with `#` to ensure they are
disambiguated from external package specifiers.

For example, the imports field can be used to gain the benefits of conditional
exports for internal modules:

```json
// package.json
{
  "imports": {
    "#dep": {
      "node": "dep-node-native",
      "default": "./dep-polyfill.js"
    }
  },
  "dependencies": {
    "dep-node-native": "^1.0.0"
  }
}
```

where `import '#dep'` does not get the resolution of the external package
`dep-node-native` (including its exports in turn), and instead gets the local
file `./dep-polyfill.js` relative to the package in other environments.

Unlike the `"exports"` field, the `"imports"` field permits mapping to external
packages.

The resolution rules for the imports field are otherwise analogous to the
exports field.
