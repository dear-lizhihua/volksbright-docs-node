#### `load(url, context, nextLoad)`

<!-- YAML
changes:
  - version:
    - v18.6.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42623
    description: Add support for chaining load hooks. Each hook must either
      call `nextLoad()` or include a `shortCircuit` property set to `true` in
      its return.
-->

> The loaders API is being redesigned. This hook may disappear or its
> signature may change. Do not rely on the API described below.

> In a previous version of this API, this was split across 3 separate, now
> deprecated, hooks (`getFormat`, `getSource`, and `transformSource`).

* `url` {string} The URL returned by the `resolve` chain
* `context` {Object}
  * `conditions` {string\[]} Export conditions of the relevant `package.json`
  * `format` {string|null|undefined} The format optionally supplied by the
    `resolve` hook chain
  * `importAssertions` {Object}
* `nextLoad` {Function} The subsequent `load` hook in the chain, or the
  Node.js default `load` hook after the last user-supplied `load` hook
  * `specifier` {string}
  * `context` {Object}
* Returns: {Object}
  * `format` {string}
  * `shortCircuit` {undefined|boolean} A signal that this hook intends to
    terminate the chain of `resolve` hooks. **Default:** `false`
  * `source` {string|ArrayBuffer|TypedArray} The source for Node.js to evaluate

The `load` hook provides a way to define a custom method of determining how
a URL should be interpreted, retrieved, and parsed. It is also in charge of
validating the import assertion.

The final value of `format` must be one of the following:

| `format`     | Description                    | Acceptable types for `source` returned by `load`      |
| ------------ | ------------------------------ | ----------------------------------------------------- |
| `'builtin'`  | Load a Node.js builtin module  | Not applicable                                        |
| `'commonjs'` | Load a Node.js CommonJS module | Not applicable                                        |
| `'json'`     | Load a JSON file               | { [`string`][], [`ArrayBuffer`][], [`TypedArray`][] } |
| `'module'`   | Load an ES module              | { [`string`][], [`ArrayBuffer`][], [`TypedArray`][] } |
| `'wasm'`     | Load a WebAssembly module      | { [`ArrayBuffer`][], [`TypedArray`][] }               |

The value of `source` is ignored for type `'builtin'` because currently it is
not possible to replace the value of a Node.js builtin (core) module. The value
of `source` is ignored for type `'commonjs'` because the CommonJS module loader
does not provide a mechanism for the ES module loader to override the
[CommonJS module return value](#commonjs-namespaces). This limitation might be
overcome in the future.

> **Caveat**: The ESM `load` hook and namespaced exports from CommonJS modules
> are incompatible. Attempting to use them together will result in an empty
> object from the import. This may be addressed in the future.

> These types all correspond to classes defined in ECMAScript.

* The specific [`ArrayBuffer`][] object is a [`SharedArrayBuffer`][].
* The specific [`TypedArray`][] object is a [`Uint8Array`][].

If the source value of a text-based format (i.e., `'json'`, `'module'`)
is not a string, it is converted to a string using [`util.TextDecoder`][].

The `load` hook provides a way to define a custom method for retrieving the
source code of an ES module specifier. This would allow a loader to potentially
avoid reading files from disk. It could also be used to map an unrecognized
format to a supported one, for example `yaml` to `module`.

```js
export async function load(url, context, nextLoad) {
  const { format } = context;

  if (Math.random() > 0.5) { // Some condition
    /*
      For some or all URLs, do some custom logic for retrieving the source.
      Always return an object of the form {
        format: <string>,
        source: <string|buffer>,
      }.
    */
    return {
      format,
      shortCircuit: true,
      source: '...',
    };
  }

  // Defer to the next hook in the chain.
  return nextLoad(url);
}
```

In a more advanced scenario, this can also be used to transform an unsupported
source to a supported one (see [Examples](#examples) below).
