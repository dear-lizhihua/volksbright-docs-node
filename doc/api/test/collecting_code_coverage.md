## Collecting code coverage

When Node.js is started with the [`--experimental-test-coverage`][]
command-line flag, code coverage is collected and statistics are reported once
all tests have completed. If the [`NODE_V8_COVERAGE`][] environment variable is
used to specify a code coverage directory, the generated V8 coverage files are
written to that directory. Node.js core modules and files within
`node_modules/` directories are not included in the coverage report. If
coverage is enabled, the coverage report is sent to any [test reporters][] via
the `'test:coverage'` event.

Coverage can be disabled on a series of lines using the following
comment syntax:

```js
/* node:coverage disable */
if (anAlwaysFalseCondition) {
  // Code in this branch will never be executed, but the lines are ignored for
  // coverage purposes. All lines following the 'disable' comment are ignored
  // until a corresponding 'enable' comment is encountered.
  console.log('this is never executed');
}
/* node:coverage enable */
```

Coverage can also be disabled for a specified number of lines. After the
specified number of lines, coverage will be automatically reenabled. If the
number of lines is not explicitly provided, a single line is ignored.

```js
/* node:coverage ignore next */
if (anAlwaysFalseCondition) { console.log('this is never executed'); }

/* node:coverage ignore next 3 */
if (anAlwaysFalseCondition) {
  console.log('this is never executed');
}
```

The test runner's code coverage functionality has the following limitations,
which will be addressed in a future Node.js release:

* Although coverage data is collected for child processes, this information is
  not included in the coverage report. Because the command line test runner uses
  child processes to execute test files, it cannot be used with
  `--experimental-test-coverage`.
* Source maps are not supported.
* Excluding specific files or directories from the coverage report is not
  supported.
