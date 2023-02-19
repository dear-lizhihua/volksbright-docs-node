## `process.exitCode`

<!-- YAML
added: v0.11.8
changes:
  - version: REPLACEME
    pr-url: https://github.com/nodejs/node/pull/43716
    description: Only accepts a code of type number, or of type string if it
                 represents an integer.
-->

* {integer|string|null|undefined} The exit code. For string type, only
  integer strings (e.g.,'1') are allowed. **Default:** `undefined`.

A number which will be the process exit code, when the process either
exits gracefully, or is exited via [`process.exit()`][] without specifying
a code.

Specifying a code to [`process.exit(code)`][`process.exit()`] will override any
previous setting of `process.exitCode`.
