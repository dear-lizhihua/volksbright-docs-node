### Main entry point export

When writing a new package, it is recommended to use the [`"exports"`][] field:

```json
{
  "exports": "./index.js"
}
```

When the [`"exports"`][] field is defined, all subpaths of the package are
encapsulated and no longer available to importers. For example,
`require('pkg/subpath.js')` throws an [`ERR_PACKAGE_PATH_NOT_EXPORTED`][]
error.

This encapsulation of exports provides more reliable guarantees
about package interfaces for tools and when handling semver upgrades for a
package. It is not a strong encapsulation since a direct require of any
absolute subpath of the package such as
`require('/path/to/node_modules/pkg/subpath.js')` will still load `subpath.js`.

All currently supported versions of Node.js and modern build tools support the
`"exports"` field. For projects using an older version of Node.js or a related
build tool, compatibility can be achieved by including the `"main"` field
alongside `"exports"` pointing to the same module:

```json
{
  "main": "./index.js",
  "exports": "./index.js"
}
```
