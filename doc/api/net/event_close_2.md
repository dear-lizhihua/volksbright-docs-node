### Event: `'close'`

<!-- YAML
added: v0.1.90
-->

* `hadError` {boolean} `true` if the socket had a transmission error.

Emitted once the socket is fully closed. The argument `hadError` is a boolean
which says if the socket was closed due to a transmission error.
