## Legacy assertion mode

Legacy assertion mode uses the [`==` operator][] in:

* [`assert.deepEqual()`][]
* [`assert.equal()`][]
* [`assert.notDeepEqual()`][]
* [`assert.notEqual()`][]

To use legacy assertion mode:

```mjs
import assert from 'node:assert';
```

```cjs
const assert = require('node:assert');
```

Legacy assertion mode may have surprising results, especially when using
[`assert.deepEqual()`][]:

```cjs
// WARNING: This does not throw an AssertionError in legacy assertion mode!
assert.deepEqual(/a/gi, new Date());
```
