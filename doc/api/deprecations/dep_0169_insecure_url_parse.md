### DEP0169: Insecure url.parse()

<!-- YAML
changes:
  - version:
      - v19.0.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/44919
    description: Documentation-only deprecation.
-->

Type: Documentation-only

[`url.parse()`][] behavior is not standardized and prone to errors that
have security implications. Use the [WHATWG URL API][] instead. CVEs are not
issued for `url.parse()` vulnerabilities.
