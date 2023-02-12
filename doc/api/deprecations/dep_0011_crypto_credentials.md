### DEP0011: `crypto.Credentials`

<!-- YAML
changes:
  - version: v11.0.0
    pr-url: https://github.com/nodejs/node/pull/21153
    description: End-of-Life.
  - version:
    - v6.12.0
    - v4.8.6
    pr-url: https://github.com/nodejs/node/pull/10116
    description: A deprecation code has been assigned.
  - version: v0.11.13
    pr-url: https://github.com/nodejs/node-v0.x-archive/pull/7265
    description: Runtime deprecation.
-->

Type: End-of-Life

The `crypto.Credentials` class was removed. Please use [`tls.SecureContext`][]
instead.
