## Test reporters

<!-- YAML
added: v19.6.0
-->

The `node:test` module supports passing [`--test-reporter`][]
flags for the test runner to use a specific reporter.

The following built-reporters are supported:

* `tap`
  The `tap` reporter is the default reporter used by the test runner. It outputs
  the test results in the [TAP][] format.

* `spec`
  The `spec` reporter outputs the test results in a human-readable format.

* `dot`
  The `dot` reporter outputs the test results in a compact format,
  where each passing test is represented by a `.`,
  and each failing test is represented by a `X`.
