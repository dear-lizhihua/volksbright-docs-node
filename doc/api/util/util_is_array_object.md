### `util.isArray(object)`

<!-- YAML
added: v0.6.0
deprecated: v4.0.0
-->

> Stability: 0 - Deprecated: Use [`Array.isArray()`][] instead.

* `object` {any}
* Returns: {boolean}

Alias for [`Array.isArray()`][].

Returns `true` if the given `object` is an `Array`. Otherwise, returns `false`.

```js
const util = require('node:util');

util.isArray([]);
// Returns: true
util.isArray(new Array());
// Returns: true
util.isArray({});
// Returns: false
```
