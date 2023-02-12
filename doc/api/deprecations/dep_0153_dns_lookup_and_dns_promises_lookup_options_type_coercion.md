### DEP0153: `dns.lookup` and `dnsPromises.lookup` options type coercion

<!-- YAML
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41431
    description: End-of-Life.
  - version: v17.0.0
    pr-url: https://github.com/nodejs/node/pull/39793
    description: Runtime deprecation.
  - version: v16.8.0
    pr-url: https://github.com/nodejs/node/pull/38906
    description: Documentation-only deprecation.
-->

Type: End-of-Life

Using a non-nullish non-integer value for `family` option, a non-nullish
non-number value for `hints` option, a non-nullish non-boolean value for `all`
option, or a non-nullish non-boolean value for `verbatim` option in
[`dns.lookup()`][] and [`dnsPromises.lookup()`][] throws an
`ERR_INVALID_ARG_TYPE` error.
