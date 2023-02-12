#### `require.cache`

<!-- YAML
added: v0.3.0
-->

* {Object}

Modules are cached in this object when they are required. By deleting a key
value from this object, the next `require` will reload the module.
This does not apply to [native addons][], for which reloading will result in an
error.

Adding or replacing entries is also possible. This cache is checked before
built-in modules and if a name matching a built-in module is added to the cache,
only `node:`-prefixed require calls are going to receive the built-in module.
Use with care!

<!-- eslint-disable node-core/no-duplicate-requires -->

```js
const assert = require('node:assert');
const realFs = require('node:fs');

const fakeFs = {};
require.cache.fs = { exports: fakeFs };

assert.strictEqual(require('fs'), fakeFs);
assert.strictEqual(require('node:fs'), realFs);
```
