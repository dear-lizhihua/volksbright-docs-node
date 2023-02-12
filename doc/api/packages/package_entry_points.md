## Package entry points

In a package's `package.json` file, two fields can define entry points for a
package: [`"main"`][] and [`"exports"`][]. Both fields apply to both ES module
and CommonJS module entry points.

The [`"main"`][] field is supported in all versions of Node.js, but its
capabilities are limited: it only defines the main entry point of the package.

The [`"exports"`][] provides a modern alternative to [`"main"`][] allowing
multiple entry points to be defined, conditional entry resolution support
between environments, and **preventing any other entry points besides those
defined in [`"exports"`][]**. This encapsulation allows module authors to
clearly define the public interface for their package.

For new packages targeting the currently supported versions of Node.js, the
[`"exports"`][] field is recommended. For packages supporting Node.js 10 and
below, the [`"main"`][] field is required. If both [`"exports"`][] and
[`"main"`][] are defined, the [`"exports"`][] field takes precedence over
[`"main"`][] in supported versions of Node.js.

[Conditional exports][] can be used within [`"exports"`][] to define different
package entry points per environment, including whether the package is
referenced via `require` or via `import`. For more information about supporting
both CommonJS and ES modules in a single package please consult
[the dual CommonJS/ES module packages section][].

Existing packages introducing the [`"exports"`][] field will prevent consumers
of the package from using any entry points that are not defined, including the
[`package.json`][] (e.g. `require('your-package/package.json')`. **This will
likely be a breaking change.**

To make the introduction of [`"exports"`][] non-breaking, ensure that every
previously supported entry point is exported. It is best to explicitly specify
entry points so that the package's public API is well-defined. For example,
a project that previously exported `main`, `lib`,
`feature`, and the `package.json` could use the following `package.exports`:

```json
{
  "name": "my-package",
  "exports": {
    ".": "./lib/index.js",
    "./lib": "./lib/index.js",
    "./lib/index": "./lib/index.js",
    "./lib/index.js": "./lib/index.js",
    "./feature": "./feature/index.js",
    "./feature/index": "./feature/index.js",
    "./feature/index.js": "./feature/index.js",
    "./package.json": "./package.json"
  }
}
```

Alternatively a project could choose to export entire folders both with and
without extensioned subpaths using export patterns:

```json
{
  "name": "my-package",
  "exports": {
    ".": "./lib/index.js",
    "./lib": "./lib/index.js",
    "./lib/*": "./lib/*.js",
    "./lib/*.js": "./lib/*.js",
    "./feature": "./feature/index.js",
    "./feature/*": "./feature/*.js",
    "./feature/*.js": "./feature/*.js",
    "./package.json": "./package.json"
  }
}
```

With the above providing backwards-compatibility for any minor package versions,
a future major change for the package can then properly restrict the exports
to only the specific feature exports exposed:

```json
{
  "name": "my-package",
  "exports": {
    ".": "./lib/index.js",
    "./feature/*.js": "./feature/*.js",
    "./feature/internal/*": null
  }
}
```
