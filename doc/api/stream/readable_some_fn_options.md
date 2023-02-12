##### `readable.some(fn[, options])`

<!-- YAML
added:
  - v17.5.0
  - v16.15.0
-->

> Stability: 1 - Experimental

* `fn` {Function|AsyncFunction} a function to call on each chunk of the stream.
  * `data` {any} a chunk of data from the stream.
  * `options` {Object}
    * `signal` {AbortSignal} aborted if the stream is destroyed allowing to
      abort the `fn` call early.
* `options` {Object}
  * `concurrency` {number} the maximum concurrent invocation of `fn` to call
    on the stream at once. **Default:** `1`.
  * `signal` {AbortSignal} allows destroying the stream if the signal is
    aborted.
* Returns: {Promise} a promise evaluating to `true` if `fn` returned a truthy
  value for at least one of the chunks.

This method is similar to `Array.prototype.some` and calls `fn` on each chunk
in the stream until the awaited return value is `true` (or any truthy value).
Once an `fn` call on a chunk awaited return value is truthy, the stream is
destroyed and the promise is fulfilled with `true`. If none of the `fn`
calls on the chunks return a truthy value, the promise is fulfilled with
`false`.

```mjs
import { Readable } from 'node:stream';
import { stat } from 'node:fs/promises';

// With a synchronous predicate.
await Readable.from([1, 2, 3, 4]).some((x) => x > 2); // true
await Readable.from([1, 2, 3, 4]).some((x) => x < 0); // false

// With an asynchronous predicate, making at most 2 file checks at a time.
const anyBigFile = await Readable.from([
  'file1',
  'file2',
  'file3',
]).some(async (fileName) => {
  const stats = await stat(fileName);
  return stat.size > 1024 * 1024;
}, { concurrency: 2 });
console.log(anyBigFile); // `true` if any file in the list is bigger than 1MB
console.log('done'); // Stream has finished
```
