### DEP0129: `ChildProcess._channel`

<!-- YAML
changes:
  - version: v13.0.0
    pr-url: https://github.com/nodejs/node/pull/27949
    description: Runtime deprecation.
  - version: v11.14.0
    pr-url: https://github.com/nodejs/node/pull/26982
    description: Documentation-only.
-->

Type: Runtime

The `_channel` property of child process objects returned by `spawn()` and
similar functions is not intended for public use. Use `ChildProcess.channel`
instead.
