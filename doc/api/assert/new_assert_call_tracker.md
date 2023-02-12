### `new assert.CallTracker()`

<!-- YAML
added:
  - v14.2.0
  - v12.19.0
-->

Creates a new [`CallTracker`][] object which can be used to track if functions
were called a specific number of times. The `tracker.verify()` must be called
for the verification to take place. The usual pattern would be to call it in a
[`process.on('exit')`][] handler.

```mjs
import assert from 'node:assert';
import process from 'node:process';

const tracker = new assert.CallTracker();

function func() {}

// callsfunc() must be called exactly 1 time before tracker.verify().
const callsfunc = tracker.calls(func, 1);

callsfunc();

// Calls tracker.verify() and verifies if all tracker.calls() functions have
// been called exact times.
process.on('exit', () => {
  tracker.verify();
});
```

```cjs
const assert = require('node:assert');

const tracker = new assert.CallTracker();

function func() {}

// callsfunc() must be called exactly 1 time before tracker.verify().
const callsfunc = tracker.calls(func, 1);

callsfunc();

// Calls tracker.verify() and verifies if all tracker.calls() functions have
// been called exact times.
process.on('exit', () => {
  tracker.verify();
});
```
