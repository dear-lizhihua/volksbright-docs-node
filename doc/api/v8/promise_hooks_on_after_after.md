### `promiseHooks.onAfter(after)`

<!-- YAML
added:
  - v17.1.0
  - v16.14.0
-->

* `after` {Function} The [`after` callback][] to call after a promise
  continuation executes.
* Returns: {Function} Call to stop the hook.

**The `after` hook must be a plain function. Providing an async function will
throw as it would produce an infinite microtask loop.**

```mjs
import { promiseHooks } from 'node:v8';

const stop = promiseHooks.onAfter((promise) => {});
```

```cjs
const { promiseHooks } = require('node:v8');

const stop = promiseHooks.onAfter((promise) => {});
```
