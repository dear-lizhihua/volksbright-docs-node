##### `readable.asIndexedPairs([options])`

<!-- YAML
added:
  - v17.5.0
  - v16.15.0
-->

> Stability: 1 - Experimental

* `options` {Object}
  * `signal` {AbortSignal} allows destroying the stream if the signal is
    aborted.
* Returns: {Readable} a stream of indexed pairs.

This method returns a new stream with chunks of the underlying stream paired
with a counter in the form `[index, chunk]`. The first index value is 0 and it
increases by 1 for each chunk produced.

```mjs
import { Readable } from 'node:stream';

const pairs = await Readable.from(['a', 'b', 'c']).asIndexedPairs().toArray();
console.log(pairs); // [[0, 'a'], [1, 'b'], [2, 'c']]
```
