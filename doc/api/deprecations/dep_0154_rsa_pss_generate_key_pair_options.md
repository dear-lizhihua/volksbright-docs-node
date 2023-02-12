### DEP0154: RSA-PSS generate key pair options

<!-- YAML
changes:
  - version: REPLACEME
    pr-url: https://github.com/nodejs/node/pull/45653
    description: Runtime deprecation.
  - version: v16.10.0
    pr-url: https://github.com/nodejs/node/pull/39927
    description: Documentation-only deprecation.
-->

Type: Runtime

The `'hash'` and `'mgf1Hash'` options are replaced with `'hashAlgorithm'`
and `'mgf1HashAlgorithm'`.
