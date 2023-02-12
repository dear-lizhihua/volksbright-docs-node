### `tracker.getCalls(fn)`

<!-- YAML
added:
  - v18.8.0
  - v16.18.0
-->

* `fn` {Function}.

* Returns: {Array} with all the calls to a tracked function.

* Object {Object}
  * `thisArg` {Object}
  * `arguments` {Array} the arguments passed to the tracked function

```mjs
import assert from 'node:assert';

const tracker = new assert.CallTracker();

function func() {}
const callsfunc = tracker.calls(func);
callsfunc(1, 2, 3);

assert.deepStrictEqual(tracker.getCalls(callsfunc),
                       [{ thisArg: this, arguments: [1, 2, 3 ] }]);
```

```cjs
const assert = require('node:assert');

// Creates call tracker.
const tracker = new assert.CallTracker();

function func() {}
const callsfunc = tracker.calls(func);
callsfunc(1, 2, 3);

assert.deepStrictEqual(tracker.getCalls(callsfunc),
                       [{ thisArg: this, arguments: [1, 2, 3 ] }]);
```
