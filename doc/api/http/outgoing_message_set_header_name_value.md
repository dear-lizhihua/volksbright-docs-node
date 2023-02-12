### `outgoingMessage.setHeader(name, value)`

<!-- YAML
added: v0.4.0
-->

* `name` {string} Header name
* `value` {any} Header value
* Returns: {this}

Sets a single header value. If the header already exists in the to-be-sent
headers, its value will be replaced. Use an array of strings to send multiple
headers with the same name.
