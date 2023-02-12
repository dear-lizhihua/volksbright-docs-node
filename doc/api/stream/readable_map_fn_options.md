##### `readable.map(fn[, options])`

<!-- YAML
added:
  - v17.4.0
  - v16.14.0
-->

> Stability: 1 - Experimental

* `fn` {Function|AsyncFunction} a function to map over every chunk in the
  stream.
  * `data` {any} a chunk of data from the stream.
  * `options` {Object}
    * `signal` {AbortSignal} aborted if the stream is destroyed allowing to
      abort the `fn` call early.
* `options` {Object}
  * `concurrency` {number} the maximum concurrent invocation of `fn` to call
    on the stream at once. **Default:** `1`.
  * `signal` {AbortSignal} allows destroying the stream if the signal is
    aborted.
* Returns: {Readable} a stream mapped with the function `fn`.

This method allows mapping over the stream. The `fn` function will be called
for every chunk in the stream. If the `fn` function returns a promise - that
promise will be `await`ed before being passed to the result stream.

```mjs
import { Readable } from 'node:stream';
import { Resolver } from 'node:dns/promises';

// With a synchronous mapper.
for await (const chunk of Readable.from([1, 2, 3, 4]).map((x) => x * 2)) {
  console.log(chunk); // 2, 4, 6, 8
}
// With an asynchronous mapper, making at most 2 queries at a time.
const resolver = new Resolver();
const dnsResults = Readable.from([
  'nodejs.org',
  'openjsf.org',
  'www.linuxfoundation.org',
]).map((domain) => resolver.resolve4(domain), { concurrency: 2 });
for await (const result of dnsResults) {
  console.log(result); // Logs the DNS result of resolver.resolve4.
}
```
