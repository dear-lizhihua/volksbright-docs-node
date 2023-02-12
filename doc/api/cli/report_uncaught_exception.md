### `--report-uncaught-exception`

<!-- YAML
added: v11.8.0
changes:
  - version:
      - v18.8.0
      - v16.18.0
    pr-url: https://github.com/nodejs/node/pull/44208
    description: Report is not generated if the uncaught exception is handled.
  - version:
     - v13.12.0
     - v12.17.0
    pr-url: https://github.com/nodejs/node/pull/32242
    description: This option is no longer experimental.
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/27312
    description: changed from `--diagnostic-report-uncaught-exception` to
                 `--report-uncaught-exception`.
-->

Enables report to be generated when the process exits due to an uncaught
exception. Useful when inspecting the JavaScript stack in conjunction with
native stack and other runtime environment data.
