## `run([options])`

<!-- YAML
added:
  - v18.9.0
  - v16.19.0
-->

* `options` {Object} Configuration options for running tests. The following
  properties are supported:
  * `concurrency` {number|boolean} If a number is provided,
    then that many files would run in parallel.
    If truthy, it would run (number of cpu cores - 1)
    files in parallel.
    If falsy, it would only run one file at a time.
    If unspecified, subtests inherit this value from their parent.
    **Default:** `true`.
  * `files`: {Array} An array containing the list of files to run.
    **Default** matching files from [test runner execution model][].
  * `signal` {AbortSignal} Allows aborting an in-progress test execution.
  * `timeout` {number} A number of milliseconds the test execution will
    fail after.
    If unspecified, subtests inherit this value from their parent.
    **Default:** `Infinity`.
  * `inspectPort` {number|Function} Sets inspector port of test child process.
    This can be a number, or a function that takes no arguments and returns a
    number. If a nullish value is provided, each process gets its own port,
    incremented from the primary's `process.debugPort`.
    **Default:** `undefined`.
* Returns: {TestsStream}

```js
run({ files: [path.resolve('./tests/test.js')] })
  .pipe(process.stdout);
```
