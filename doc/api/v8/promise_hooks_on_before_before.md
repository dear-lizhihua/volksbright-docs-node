### `promiseHooks.onBefore(before)`

<!-- YAML
added:
  - v17.1.0
  - v16.14.0
-->

* `before` {Function} The [`before` callback][] to call before a promise
  continuation executes.
* Returns: {Function} Call to stop the hook.

**The `before` hook must be a plain function. Providing an async function will
throw as it would produce an infinite microtask loop.**

```mjs
import { promiseHooks } from 'node:v8';

const stop = promiseHooks.onBefore((promise) => {});
```

```cjs
const { promiseHooks } = require('node:v8');

const stop = promiseHooks.onBefore((promise) => {});
```
