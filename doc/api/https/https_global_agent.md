## `https.globalAgent`

<!-- YAML
added: v0.5.9
changes:
  - version:
      - v19.0.0
    pr-url: https://github.com/nodejs/node/pull/43522
    description: The agent now uses HTTP Keep-Alive by default.
-->

Global instance of [`https.Agent`][] for all HTTPS client requests.
