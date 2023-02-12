### `tracker.reset([fn])`

<!-- YAML
added:
  - v18.8.0
  - v16.18.0
-->

* `fn` {Function} a tracked function to reset.

reset calls of the call tracker.
if a tracked function is passed as an argument, the calls will be reset for it.
if no arguments are passed, all tracked functions will be reset

```mjs
import assert from 'node:assert';

const tracker = new assert.CallTracker();

function func() {}
const callsfunc = tracker.calls(func);

callsfunc();
// Tracker was called once
tracker.getCalls(callsfunc).length === 1;

tracker.reset(callsfunc);
tracker.getCalls(callsfunc).length === 0;
```

```cjs
const assert = require('node:assert');

function func() {}
const callsfunc = tracker.calls(func);

callsfunc();
// Tracker was called once
tracker.getCalls(callsfunc).length === 1;

tracker.reset(callsfunc);
tracker.getCalls(callsfunc).length === 0;
```
