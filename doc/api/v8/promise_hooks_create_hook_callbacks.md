### `promiseHooks.createHook(callbacks)`

<!-- YAML
added:
  - v17.1.0
  - v16.14.0
-->

* `callbacks` {Object} The [Hook Callbacks][] to register
  * `init` {Function} The [`init` callback][].
  * `before` {Function} The [`before` callback][].
  * `after` {Function} The [`after` callback][].
  * `settled` {Function} The [`settled` callback][].
* Returns: {Function} Used for disabling hooks

**The hook callbacks must be plain functions. Providing async functions will
throw as it would produce an infinite microtask loop.**

Registers functions to be called for different lifetime events of each promise.

The callbacks `init()`/`before()`/`after()`/`settled()` are called for the
respective events during a promise's lifetime.

All callbacks are optional. For example, if only promise creation needs to
be tracked, then only the `init` callback needs to be passed. The
specifics of all functions that can be passed to `callbacks` is in the
[Hook Callbacks][] section.

```mjs
import { promiseHooks } from 'node:v8';

const stopAll = promiseHooks.createHook({
  init(promise, parent) {},
});
```

```cjs
const { promiseHooks } = require('node:v8');

const stopAll = promiseHooks.createHook({
  init(promise, parent) {},
});
```
