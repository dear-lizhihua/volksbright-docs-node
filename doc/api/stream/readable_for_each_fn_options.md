##### `readable.forEach(fn[, options])`

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
* Returns: {Promise} a promise for when the stream has finished.

This method allows iterating a stream. For each chunk in the stream the
`fn` function will be called. If the `fn` function returns a promise - that
promise will be `await`ed.

This method is different from `for await...of` loops in that it can optionally
process chunks concurrently. In addition, a `forEach` iteration can only be
stopped by having passed a `signal` option and aborting the related
`AbortController` while `for await...of` can be stopped with `break` or
`return`. In either case the stream will be destroyed.

This method is different from listening to the [`'data'`][] event in that it
uses the [`readable`][] event in the underlying machinary and can limit the
number of concurrent `fn` calls.

```mjs
import { Readable } from 'node:stream';
import { Resolver } from 'node:dns/promises';

// With a synchronous predicate.
for await (const chunk of Readable.from([1, 2, 3, 4]).filter((x) => x > 2)) {
  console.log(chunk); // 3, 4
}
// With an asynchronous predicate, making at most 2 queries at a time.
const resolver = new Resolver();
const dnsResults = Readable.from([
  'nodejs.org',
  'openjsf.org',
  'www.linuxfoundation.org',
]).map(async (domain) => {
  const { address } = await resolver.resolve4(domain, { ttl: true });
  return address;
}, { concurrency: 2 });
await dnsResults.forEach((result) => {
  // Logs result, similar to `for await (const result of dnsResults)`
  console.log(result);
});
console.log('done'); // Stream has finished
```
