### `--test`

<!-- YAML
added:
  - v18.1.0
  - v16.17.0
changes:
  - version:
      - v19.2.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/45214
    description: Test runner now supports running in watch mode.
-->

Starts the Node.js command line test runner. This flag cannot be combined with
`--watch-path`, `--check`, `--eval`, `--interactive`, or the inspector.
See the documentation on [running tests from the command line][]
for more details.
