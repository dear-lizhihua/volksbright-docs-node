### `promiseHooks.onInit(init)`

<!-- YAML
added:
  - v17.1.0
  - v16.14.0
-->

* `init` {Function} The [`init` callback][] to call when a promise is created.
* Returns: {Function} Call to stop the hook.

**The `init` hook must be a plain function. Providing an async function will
throw as it would produce an infinite microtask loop.**

```mjs
import { promiseHooks } from 'node:v8';

const stop = promiseHooks.onInit((promise, parent) => {});
```

```cjs
const { promiseHooks } = require('node:v8');

const stop = promiseHooks.onInit((promise, parent) => {});
```
