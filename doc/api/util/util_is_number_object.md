### `util.isNumber(object)`

<!-- YAML
added: v0.11.5
deprecated: v4.0.0
-->

> Stability: 0 - Deprecated: Use `typeof value === 'number'` instead.

* `object` {any}
* Returns: {boolean}

Returns `true` if the given `object` is a `Number`. Otherwise, returns `false`.

```js
const util = require('node:util');

util.isNumber(false);
// Returns: false
util.isNumber(Infinity);
// Returns: true
util.isNumber(0);
// Returns: true
util.isNumber(NaN);
// Returns: true
```
