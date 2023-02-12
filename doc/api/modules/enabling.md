## Enabling

<!-- type=misc -->

Node.js has two module systems: CommonJS modules and [ECMAScript modules][].

By default, Node.js will treat the following as CommonJS modules:

* Files with a `.cjs` extension;

* Files with a `.js` extension when the nearest parent `package.json` file
  contains a top-level field [`"type"`][] with a value of `"commonjs"`.

* Files with a `.js` extension when the nearest parent `package.json` file
  doesn't contain a top-level field [`"type"`][]. Package authors should include
  the [`"type"`][] field, even in packages where all sources are CommonJS. Being
  explicit about the `type` of the package will make things easier for build
  tools and loaders to determine how the files in the package should be
  interpreted.

* Files with an extension that is not `.mjs`, `.cjs`, `.json`, `.node`, or `.js`
  (when the nearest parent `package.json` file contains a top-level field
  [`"type"`][] with a value of `"module"`, those files will be recognized as
  CommonJS modules only if they are being included via `require()`, not when
  used as the command-line entry point of the program).

See [Determining module system][] for more details.

Calling `require()` always use the CommonJS module loader. Calling `import()`
always use the ECMAScript module loader.
