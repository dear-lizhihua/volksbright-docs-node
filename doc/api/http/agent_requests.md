### `agent.requests`

<!-- YAML
added: v0.5.9
changes:
  - version: v16.0.0
    pr-url: https://github.com/nodejs/node/pull/36409
    description: The property now has a `null` prototype.
-->

* {Object}

An object which contains queues of requests that have not yet been assigned to
sockets. Do not modify.
