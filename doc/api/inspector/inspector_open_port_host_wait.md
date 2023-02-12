### `inspector.open([port[, host[, wait]]])`

* `port` {number} Port to listen on for inspector connections. Optional.
  **Default:** what was specified on the CLI.
* `host` {string} Host to listen on for inspector connections. Optional.
  **Default:** what was specified on the CLI.
* `wait` {boolean} Block until a client has connected. Optional.
  **Default:** `false`.

Activate inspector on host and port. Equivalent to
`node --inspect=[[host:]port]`, but can be done programmatically after node has
started.

If wait is `true`, will block until a client has connected to the inspect port
and flow control has been passed to the debugger client.

See the [security warning][] regarding the `host`
parameter usage.
