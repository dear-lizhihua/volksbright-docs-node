##### `readable.drop(limit[, options])`

<!-- YAML
added:
  - v17.5.0
  - v16.15.0
-->

> Stability: 1 - Experimental

* `limit` {number} the number of chunks to drop from the readable.
* `options` {Object}
  * `signal` {AbortSignal} allows destroying the stream if the signal is
    aborted.
* Returns: {Readable} a stream with `limit` chunks dropped.

This method returns a new stream with the first `limit` chunks dropped.

```mjs
import { Readable } from 'node:stream';

await Readable.from([1, 2, 3, 4]).drop(2).toArray(); // [3, 4]
```
