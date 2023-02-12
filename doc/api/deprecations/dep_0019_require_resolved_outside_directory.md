### DEP0019: `require('.')` resolved outside directory

<!-- YAML
changes:
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/26973
    description: Removed functionality.
  - version:
    - v6.12.0
    - v4.8.6
    pr-url: https://github.com/nodejs/node/pull/10116
    description: A deprecation code has been assigned.
  - version: v1.8.1
    pr-url: https://github.com/nodejs/node/pull/1363
    description: Runtime deprecation.
-->

Type: End-of-Life

In certain cases, `require('.')` could resolve outside the package directory.
This behavior has been removed.
