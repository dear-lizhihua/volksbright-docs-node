### `script.createCachedData()`

<!-- YAML
added: v10.6.0
-->

* Returns: {Buffer}

Creates a code cache that can be used with the `Script` constructor's
`cachedData` option. Returns a `Buffer`. This method may be called at any
time and any number of times.

The code cache of the `Script` doesn't contain any JavaScript observable
states. The code cache is safe to be saved along side the script source and
used to construct new `Script` instances multiple times.

Functions in the `Script` source can be marked as lazily compiled and they are
not compiled at construction of the `Script`. These functions are going to be
compiled when they are invoked the first time. The code cache serializes the
metadata that V8 currently knows about the `Script` that it can use to speed up
future compilations.

```js
const script = new vm.Script(`
function add(a, b) {
  return a + b;
}

const x = add(1, 2);
`);

const cacheWithoutAdd = script.createCachedData();
// In `cacheWithoutAdd` the function `add()` is marked for full compilation
// upon invocation.

script.runInThisContext();

const cacheWithAdd = script.createCachedData();
// `cacheWithAdd` contains fully compiled function `add()`.
```
