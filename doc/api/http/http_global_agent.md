## `http.globalAgent`

<!-- YAML
added: v0.5.9
changes:
  - version:
      - v19.0.0
    pr-url: https://github.com/nodejs/node/pull/43522
    description: The agent now uses HTTP Keep-Alive by default.
-->

* {http.Agent}

Global instance of `Agent` which is used as the default for all HTTP client
requests.
