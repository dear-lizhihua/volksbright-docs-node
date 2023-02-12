## Class: `MockTracker`

<!-- YAML
added:
  - v19.1.0
  - v18.13.0
-->

The `MockTracker` class is used to manage mocking functionality. The test runner
module provides a top level `mock` export which is a `MockTracker` instance.
Each test also provides its own `MockTracker` instance via the test context's
`mock` property.
