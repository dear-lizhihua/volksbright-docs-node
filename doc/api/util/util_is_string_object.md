### `util.isString(object)`

<!-- YAML
added: v0.11.5
deprecated: v4.0.0
-->

> Stability: 0 - Deprecated: Use `typeof value === 'string'` instead.

* `object` {any}
* Returns: {boolean}

Returns `true` if the given `object` is a `string`. Otherwise, returns `false`.

```js
const util = require('node:util');

util.isString('');
// Returns: true
util.isString('foo');
// Returns: true
util.isString(String('foo'));
// Returns: true
util.isString(5);
// Returns: false
```
