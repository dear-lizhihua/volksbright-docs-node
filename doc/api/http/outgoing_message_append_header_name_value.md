### `outgoingMessage.appendHeader(name, value)`

<!-- YAML
added:
  - v18.3.0
  - v16.17.0
-->

* `name` {string} Header name
* `value` {string|string\[]} Header value
* Returns: {this}

Append a single header value for the header object.

If the value is an array, this is equivalent of calling this method multiple
times.

If there were no previous value for the header, this is equivalent of calling
[`outgoingMessage.setHeader(name, value)`][].

Depending of the value of `options.uniqueHeaders` when the client request or the
server were created, this will end up in the header being sent multiple times or
a single time with values joined using `; `.
