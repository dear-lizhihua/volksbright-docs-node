### `agent.maxSockets`

<!-- YAML
added: v0.3.6
-->

* {number}

By default set to `Infinity`. Determines how many concurrent sockets the agent
can have open per origin. Origin is the returned value of [`agent.getName()`][].
