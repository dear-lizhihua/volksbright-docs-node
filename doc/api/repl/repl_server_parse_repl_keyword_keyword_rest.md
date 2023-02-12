### `replServer.parseREPLKeyword(keyword[, rest])`

<!-- YAML
added: v0.8.9
deprecated: v9.0.0
-->

> Stability: 0 - Deprecated.

* `keyword` {string} the potential keyword to parse and execute
* `rest` {any} any parameters to the keyword command
* Returns: {boolean}

An internal method used to parse and execute `REPLServer` keywords.
Returns `true` if `keyword` is a valid keyword, otherwise `false`.
