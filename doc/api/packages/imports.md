### `"imports"`

<!-- YAML
added:
 - v14.6.0
 - v12.19.0
-->

* Type: {Object}

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

Entries in the imports field must be strings starting with `#`.

Package imports permit mapping to external packages.

This field defines [subpath imports][] for the current package.

[Babel]: https://babeljs.io/
[CommonJS]: modules.md
[Conditional exports]: #conditional-exports
[Corepack]: corepack.md
[ES module]: esm.md
[ES modules]: esm.md
[Node.js documentation for this section]: https://github.com/nodejs/node/blob/HEAD/doc/api/packages.md#conditions-definitions
[`"exports"`]: #exports
[`"imports"`]: #imports
[`"main"`]: #main
[`"name"`]: #name
[`"packageManager"`]: #packagemanager
[`"type"`]: #type
[`--conditions` / `-C` flag]: #resolving-user-conditions
[`--no-addons` flag]: cli.md#--no-addons
[`ERR_PACKAGE_PATH_NOT_EXPORTED`]: errors.md#err_package_path_not_exported
[`esm`]: https://github.com/standard-things/esm#readme
[`package.json`]: #nodejs-packagejson-field-definitions
[entry points]: #package-entry-points
[folders as modules]: modules.md#folders-as-modules
[import maps]: https://github.com/WICG/import-maps
[load ECMASCript modules from CommonJS modules]: modules.md#the-mjs-extension
[loader hooks]: esm.md#loaders
[packages folder mapping]: https://github.com/WICG/import-maps#packages-via-trailing-slashes
[self-reference]: #self-referencing-a-package-using-its-name
[subpath exports]: #subpath-exports
[subpath imports]: #subpath-imports
[supported package managers]: corepack.md#supported-package-managers
[the dual CommonJS/ES module packages section]: #dual-commonjses-module-packages
[the full specifier path]: esm.md#mandatory-file-extensions
