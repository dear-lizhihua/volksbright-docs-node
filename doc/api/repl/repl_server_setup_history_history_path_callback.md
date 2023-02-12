### `replServer.setupHistory(historyPath, callback)`

<!-- YAML
added: v11.10.0
-->

* `historyPath` {string} the path to the history file
* `callback` {Function} called when history writes are ready or upon error
  * `err` {Error}
  * `repl` {repl.REPLServer}

Initializes a history log file for the REPL instance. When executing the
Node.js binary and using the command-line REPL, a history file is initialized
by default. However, this is not the case when creating a REPL
programmatically. Use this method to initialize a history log file when working
with REPL instances programmatically.
