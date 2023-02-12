### DEP0071: `async_hooks.triggerId()`

<!-- YAML
changes:
  - version: v9.0.0
    pr-url: https://github.com/nodejs/node/pull/14414
    description: End-of-Life.
  - version: v8.2.0
    pr-url: https://github.com/nodejs/node/pull/13490
    description: Runtime deprecation.
-->

Type: End-of-Life

`async_hooks.triggerId()` was renamed to `async_hooks.triggerAsyncId()` for
clarity.

This change was made while `async_hooks` was an experimental API.
