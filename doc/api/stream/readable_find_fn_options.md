##### `readable.find(fn[, options])`

<!-- YAML
added:
  - v17.5.0
  - v16.17.0
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
* Returns: {Promise} a promise evaluating to the first chunk for which `fn`
  evaluated with a truthy value, or `undefined` if no element was found.

This method is similar to `Array.prototype.find` and calls `fn` on each chunk
in the stream to find a chunk with a truthy value for `fn`. Once an `fn` call's
awaited return value is truthy, the stream is destroyed and the promise is
fulfilled with value for which `fn` returned a truthy value. If all of the
`fn` calls on the chunks return a falsy value, the promise is fulfilled with
`undefined`.

```mjs
import { Readable } from 'node:stream';
import { stat } from 'node:fs/promises';

// With a synchronous predicate.
await Readable.from([1, 2, 3, 4]).find((x) => x > 2); // 3
await Readable.from([1, 2, 3, 4]).find((x) => x > 0); // 1
await Readable.from([1, 2, 3, 4]).find((x) => x > 10); // undefined

// With an asynchronous predicate, making at most 2 file checks at a time.
const foundBigFile = await Readable.from([
  'file1',
  'file2',
  'file3',
]).find(async (fileName) => {
  const stats = await stat(fileName);
  return stat.size > 1024 * 1024;
}, { concurrency: 2 });
console.log(foundBigFile); // File name of large file, if any file in the list is bigger than 1MB
console.log('done'); // Stream has finished
```
