### `promiseHooks.onSettled(settled)`

<!-- YAML
added:
  - v17.1.0
  - v16.14.0
-->

* `settled` {Function} The [`settled` callback][] to call when a promise
  is resolved or rejected.
* Returns: {Function} Call to stop the hook.

**The `settled` hook must be a plain function. Providing an async function will
throw as it would produce an infinite microtask loop.**

```mjs
import { promiseHooks } from 'node:v8';

const stop = promiseHooks.onSettled((promise) => {});
```

```cjs
const { promiseHooks } = require('node:v8');

const stop = promiseHooks.onSettled((promise) => {});
```
