### DEP0170: Invalid port when using `url.parse()`

<!-- YAML
changes:
  - version:
    - REPLACEME
    pr-url: https://github.com/nodejs/node/pull/45526
    description: Runtime deprecation.
  - version:
      - v19.2.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/45576
    description: Documentation-only deprecation.
-->

Type: Runtime

[`url.parse()`][] accepts URLs with ports that are not numbers. This behavior
might result in host name spoofing with unexpected input. These URLs will throw
an error in future versions of Node.js, as the [WHATWG URL API][] does already.
