### `sourceTextModule.createCachedData()`

<!-- YAML
added:
 - v13.7.0
 - v12.17.0
-->

* Returns: {Buffer}

Creates a code cache that can be used with the `SourceTextModule` constructor's
`cachedData` option. Returns a `Buffer`. This method may be called any number
of times before the module has been evaluated.

The code cache of the `SourceTextModule` doesn't contain any JavaScript
observable states. The code cache is safe to be saved along side the script
source and used to construct new `SourceTextModule` instances multiple times.

Functions in the `SourceTextModule` source can be marked as lazily compiled
and they are not compiled at construction of the `SourceTextModule`. These
functions are going to be compiled when they are invoked the first time. The
code cache serializes the metadata that V8 currently knows about the
`SourceTextModule` that it can use to speed up future compilations.

```js
// Create an initial module
const module = new vm.SourceTextModule('const a = 1;');

// Create cached data from this module
const cachedData = module.createCachedData();

// Create a new module using the cached data. The code must be the same.
const module2 = new vm.SourceTextModule('const a = 1;', { cachedData });
```
