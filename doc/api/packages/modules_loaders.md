### Modules loaders

Node.js has two systems for resolving a specifier and loading modules.

There is the CommonJS module loader:

* It is fully synchronous.
* It is responsible for handling `require()` calls.
* It is monkey patchable.
* It supports [folders as modules][].
* When resolving a specifier, if no exact match is found, it will try to add
  extensions (`.js`, `.json`, and finally `.node`) and then attempt to resolve
  [folders as modules][].
* It treats `.json` as JSON text files.
* `.node` files are interpreted as compiled addon modules loaded with
  `process.dlopen()`.
* It treats all files that lack `.json` or `.node` extensions as JavaScript
  text files.
* It cannot be used to load ECMAScript modules (although it is possible to
  [load ECMASCript modules from CommonJS modules][]). When used to load a
  JavaScript text file that is not an ECMAScript module, it loads it as a
  CommonJS module.

There is the ECMAScript module loader:

* It is asynchronous.
* It is responsible for handling `import` statements and `import()` expressions.
* It is not monkey patchable, can be customized using [loader hooks][].
* It does not support folders as modules, directory indexes (e.g.
  `'./startup/index.js'`) must be fully specified.
* It does no extension searching. A file extension must be provided
  when the specifier is a relative or absolute file URL.
* It can load JSON modules, but an import assertion is required.
* It accepts only `.js`, `.mjs`, and `.cjs` extensions for JavaScript text
  files.
* It can be used to load JavaScript CommonJS modules. Such modules
  are passed through the `cjs-module-lexer` to try to identify named exports,
  which are available if they can be determined through static analysis.
  Imported CommonJS modules have their URLs converted to absolute
  paths and are then loaded via the CommonJS module loader.
