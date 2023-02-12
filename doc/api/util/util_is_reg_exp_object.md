### `util.isRegExp(object)`

<!-- YAML
added: v0.6.0
deprecated: v4.0.0
-->

> Stability: 0 - Deprecated

* `object` {any}
* Returns: {boolean}

Returns `true` if the given `object` is a `RegExp`. Otherwise, returns `false`.

```js
const util = require('node:util');

util.isRegExp(/some regexp/);
// Returns: true
util.isRegExp(new RegExp('another regexp'));
// Returns: true
util.isRegExp({});
// Returns: false
```
