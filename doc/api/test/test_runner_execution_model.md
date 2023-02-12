### Test runner execution model

When searching for test files to execute, the test runner behaves as follows:

* Any files explicitly provided by the user are executed.
* If the user did not explicitly specify any paths, the current working
  directory is recursively searched for files as specified in the following
  steps.
* `node_modules` directories are skipped unless explicitly provided by the
  user.
* If a directory named `test` is encountered, the test runner will search it
  recursively for all all `.js`, `.cjs`, and `.mjs` files. All of these files
  are treated as test files, and do not need to match the specific naming
  convention detailed below. This is to accommodate projects that place all of
  their tests in a single `test` directory.
* In all other directories, `.js`, `.cjs`, and `.mjs` files matching the
  following patterns are treated as test files:
  * `^test$` - Files whose basename is the string `'test'`. Examples:
    `test.js`, `test.cjs`, `test.mjs`.
  * `^test-.+` - Files whose basename starts with the string `'test-'`
    followed by one or more characters. Examples: `test-example.js`,
    `test-another-example.mjs`.
  * `.+[\.\-\_]test$` - Files whose basename ends with `.test`, `-test`, or
    `_test`, preceded by one or more characters. Examples: `example.test.js`,
    `example-test.cjs`, `example_test.mjs`.
  * Other file types understood by Node.js such as `.node` and `.json` are not
    automatically executed by the test runner, but are supported if explicitly
    provided on the command line.

Each matching test file is executed in a separate child process. If the child
process finishes with an exit code of 0, the test is considered passing.
Otherwise, the test is considered to be a failure. Test files must be
executable by Node.js, but are not required to use the `node:test` module
internally.
