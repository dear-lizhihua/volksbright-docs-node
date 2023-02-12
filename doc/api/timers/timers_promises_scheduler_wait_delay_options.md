### `timersPromises.scheduler.wait(delay[, options])`

<!-- YAML
added:
  - v17.3.0
  - v16.14.0
-->

> Stability: 1 - Experimental

* `delay` {number} The number of milliseconds to wait before resolving the
  promise.
* `options` {Object}
  * `signal` {AbortSignal} An optional `AbortSignal` that can be used to
    cancel waiting.
* Returns: {Promise}

An experimental API defined by the [Scheduling APIs][] draft specification
being developed as a standard Web Platform API.

Calling `timersPromises.scheduler.wait(delay, options)` is roughly equivalent
to calling `timersPromises.setTimeout(delay, undefined, options)` except that
the `ref` option is not supported.

```mjs
import { scheduler } from 'node:timers/promises';

await scheduler.wait(1000); // Wait one second before continuing
```
