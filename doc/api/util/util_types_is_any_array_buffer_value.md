### `util.types.isAnyArrayBuffer(value)`

<!-- YAML
added: v10.0.0
-->

* `value` {any}
* Returns: {boolean}

Returns `true` if the value is a built-in [`ArrayBuffer`][] or
[`SharedArrayBuffer`][] instance.

See also [`util.types.isArrayBuffer()`][] and
[`util.types.isSharedArrayBuffer()`][].

```js
util.types.isAnyArrayBuffer(new ArrayBuffer());  // Returns true
util.types.isAnyArrayBuffer(new SharedArrayBuffer());  // Returns true
```
