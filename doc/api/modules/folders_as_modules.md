## Folders as modules

<!--type=misc-->

> Stability: 3 - Legacy: Use [subpath exports][] or [subpath imports][] instead.

There are three ways in which a folder may be passed to `require()` as
an argument.

The first is to create a [`package.json`][] file in the root of the folder,
which specifies a `main` module. An example [`package.json`][] file might
look like this:

```json
{ "name" : "some-library",
  "main" : "./lib/some-library.js" }
```

If this was in a folder at `./some-library`, then
`require('./some-library')` would attempt to load
`./some-library/lib/some-library.js`.

If there is no [`package.json`][] file present in the directory, or if the
[`"main"`][] entry is missing or cannot be resolved, then Node.js
will attempt to load an `index.js` or `index.node` file out of that
directory. For example, if there was no [`package.json`][] file in the previous
example, then `require('./some-library')` would attempt to load:

* `./some-library/index.js`
* `./some-library/index.node`

If these attempts fail, then Node.js will report the entire module as missing
with the default error:

```console
Error: Cannot find module 'some-library'
```

In all three above cases, an `import('./some-library')` call would result in a
[`ERR_UNSUPPORTED_DIR_IMPORT`][] error. Using package [subpath exports][] or
[subpath imports][] can provide the same containment organization benefits as
folders as modules, and work for both `require` and `import`.
