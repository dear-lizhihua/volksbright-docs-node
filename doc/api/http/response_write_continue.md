### `response.writeContinue()`

<!-- YAML
added: v0.3.0
-->

Sends an HTTP/1.1 100 Continue message to the client, indicating that
the request body should be sent. See the [`'checkContinue'`][] event on
`Server`.
