##### `readable.reduce(fn[, initial[, options]])`

<!-- YAML
added:
  - v17.5.0
  - v16.15.0
-->

> Stability: 1 - Experimental

* `fn` {Function|AsyncFunction} a reducer function to call over every chunk
  in the stream.
  * `previous` {any} the value obtained from the last call to `fn` or the
    `initial` value if specified or the first chunk of the stream otherwise.
  * `data` {any} a chunk of data from the stream.
  * `options` {Object}
    * `signal` {AbortSignal} aborted if the stream is destroyed allowing to
      abort the `fn` call early.
* `initial` {any} the initial value to use in the reduction.
* `options` {Object}
  * `signal` {AbortSignal} allows destroying the stream if the signal is
    aborted.
* Returns: {Promise} a promise for the final value of the reduction.

This method calls `fn` on each chunk of the stream in order, passing it the
result from the calculation on the previous element. It returns a promise for
the final value of the reduction.

The reducer function iterates the stream element-by-element which means that
there is no `concurrency` parameter or parallelism. To perform a `reduce`
concurrently, it can be chained to the [`readable.map`][] method.

If no `initial` value is supplied the first chunk of the stream is used as the
initial value. If the stream is empty, the promise is rejected with a
`TypeError` with the `ERR_INVALID_ARGS` code property.

```mjs
import { Readable } from 'node:stream';

const ten = await Readable.from([1, 2, 3, 4]).reduce((previous, data) => {
  return previous + data;
});
console.log(ten); // 10
```
