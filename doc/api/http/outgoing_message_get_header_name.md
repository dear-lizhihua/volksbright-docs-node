### `outgoingMessage.getHeader(name)`

<!-- YAML
added: v0.4.0
-->

* `name` {string} Name of header
* Returns {string | undefined}

Gets the value of the HTTP header with the given name. If that header is not
set, the returned value will be `undefined`.
