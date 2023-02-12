## Filtering tests by name

The [`--test-name-pattern`][] command-line option can be used to only run tests
whose name matches the provided pattern. Test name patterns are interpreted as
JavaScript regular expressions. The `--test-name-pattern` option can be
specified multiple times in order to run nested tests. For each test that is
executed, any corresponding test hooks, such as `beforeEach()`, are also
run.

Given the following test file, starting Node.js with the
`--test-name-pattern="test [1-3]"` option would cause the test runner to execute
`test 1`, `test 2`, and `test 3`. If `test 1` did not match the test name
pattern, then its subtests would not execute, despite matching the pattern. The
same set of tests could also be executed by passing `--test-name-pattern`
multiple times (e.g. `--test-name-pattern="test 1"`,
`--test-name-pattern="test 2"`, etc.).

```js
test('test 1', async (t) => {
  await t.test('test 2');
  await t.test('test 3');
});

test('Test 4', async (t) => {
  await t.test('Test 5');
  await t.test('test 6');
});
```

Test name patterns can also be specified using regular expression literals. This
allows regular expression flags to be used. In the previous example, starting
Node.js with `--test-name-pattern="/test [4-5]/i"` would match `Test 4` and
`Test 5` because the pattern is case-insensitive.

Test name patterns do not change the set of files that the test runner executes.
