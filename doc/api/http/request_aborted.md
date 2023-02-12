### `request.aborted`

<!-- YAML
added: v0.11.14
deprecated:
  - v17.0.0
  - v16.12.0
changes:
  - version: v11.0.0
    pr-url: https://github.com/nodejs/node/pull/20230
    description: The `aborted` property is no longer a timestamp number.
-->

> Stability: 0 - Deprecated. Check [`request.destroyed`][] instead.

* {boolean}

The `request.aborted` property will be `true` if the request has
been aborted.
