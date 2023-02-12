### DEP0115: `crypto.prng()`, `crypto.pseudoRandomBytes()`, `crypto.rng()`

<!-- YAML
changes:
  - version: v11.0.0
    pr-url:
      - https://github.com/nodejs/node/pull/22519
      - https://github.com/nodejs/node/pull/23017
    description: Added documentation-only deprecation
                 with `--pending-deprecation` support.
-->

Type: Documentation-only (supports [`--pending-deprecation`][])

<!--lint enable nodejs-yaml-comments -->

In recent versions of Node.js, there is no difference between
[`crypto.randomBytes()`][] and `crypto.pseudoRandomBytes()`. The latter is
deprecated along with the undocumented aliases `crypto.prng()` and
`crypto.rng()` in favor of [`crypto.randomBytes()`][] and might be removed in a
future release.
