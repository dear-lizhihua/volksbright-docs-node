### Environment variable options

Various behaviors of the Node.js REPL can be customized using the following
environment variables:

* `NODE_REPL_HISTORY`: When a valid path is given, persistent REPL history
  will be saved to the specified file rather than `.node_repl_history` in the
  user's home directory. Setting this value to `''` (an empty string) will
  disable persistent REPL history. Whitespace will be trimmed from the value.
  On Windows platforms environment variables with empty values are invalid so
  set this variable to one or more spaces to disable persistent REPL history.
* `NODE_REPL_HISTORY_SIZE`: Controls how many lines of history will be
  persisted if history is available. Must be a positive number.
  **Default:** `1000`.
* `NODE_REPL_MODE`: May be either `'sloppy'` or `'strict'`. **Default:**
  `'sloppy'`, which will allow non-strict mode code to be run.
