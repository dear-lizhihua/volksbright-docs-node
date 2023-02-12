## `v8.takeCoverage()`

<!-- YAML
added:
  - v15.1.0
  - v14.18.0
  - v12.22.0
-->

The `v8.takeCoverage()` method allows the user to write the coverage started by
[`NODE_V8_COVERAGE`][] to disk on demand. This method can be invoked multiple
times during the lifetime of the process. Each time the execution counter will
be reset and a new coverage report will be written to the directory specified
by [`NODE_V8_COVERAGE`][].

When the process is about to exit, one last coverage will still be written to
disk unless [`v8.stopCoverage()`][] is invoked before the process exits.
