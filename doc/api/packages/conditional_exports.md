### Conditional exports

<!-- YAML
added:
  - v13.2.0
  - v12.16.0
changes:
  - version:
    - v13.7.0
    - v12.16.0
    pr-url: https://github.com/nodejs/node/pull/31001
    description: Unflag conditional exports.
-->

Conditional exports provide a way to map to different paths depending on
certain conditions. They are supported for both CommonJS and ES module imports.

For example, a package that wants to provide different ES module exports for
`require()` and `import` can be written:

```json
// package.json
{
  "exports": {
    "import": "./index-module.js",
    "require": "./index-require.cjs"
  },
  "type": "module"
}
```

Node.js implements the following conditions, listed in order from most
specific to least specific as conditions should be defined:

* `"node-addons"` - similar to `"node"` and matches for any Node.js environment.
  This condition can be used to provide an entry point which uses native C++
  addons as opposed to an entry point which is more universal and doesn't rely
  on native addons. This condition can be disabled via the
  [`--no-addons` flag][].
* `"node"` - matches for any Node.js environment. Can be a CommonJS or ES
  module file. _In most cases explicitly calling out the Node.js platform is
  not necessary._
* `"import"` - matches when the package is loaded via `import` or
  `import()`, or via any top-level import or resolve operation by the
  ECMAScript module loader. Applies regardless of the module format of the
  target file. _Always mutually exclusive with `"require"`._
* `"require"` - matches when the package is loaded via `require()`. The
  referenced file should be loadable with `require()` although the condition
  matches regardless of the module format of the target file. Expected
  formats include CommonJS, JSON, and native addons but not ES modules as
  `require()` doesn't support them. _Always mutually exclusive with
  `"import"`._
* `"default"` - the generic fallback that always matches. Can be a CommonJS
  or ES module file. _This condition should always come last._

Within the [`"exports"`][] object, key order is significant. During condition
matching, earlier entries have higher priority and take precedence over later
entries. _The general rule is that conditions should be from most specific to
least specific in object order_.

Using the `"import"` and `"require"` conditions can lead to some hazards,
which are further explained in [the dual CommonJS/ES module packages section][].

The `"node-addons"` condition can be used to provide an entry point which
uses native C++ addons. However, this condition can be disabled via the
[`--no-addons` flag][]. When using `"node-addons"`, it's recommended to treat
`"default"` as an enhancement that provides a more universal entry point, e.g.
using WebAssembly instead of a native addon.

Conditional exports can also be extended to exports subpaths, for example:

```json
{
  "exports": {
    ".": "./index.js",
    "./feature.js": {
      "node": "./feature-node.js",
      "default": "./feature.js"
    }
  }
}
```

Defines a package where `require('pkg/feature.js')` and
`import 'pkg/feature.js'` could provide different implementations between
Node.js and other JS environments.

When using environment branches, always include a `"default"` condition where
possible. Providing a `"default"` condition ensures that any unknown JS
environments are able to use this universal implementation, which helps avoid
these JS environments from having to pretend to be existing environments in
order to support packages with conditional exports. For this reason, using
`"node"` and `"default"` condition branches is usually preferable to using
`"node"` and `"browser"` condition branches.
