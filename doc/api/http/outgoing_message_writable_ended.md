### `outgoingMessage.writableEnded`

<!-- YAML
added: v12.9.0
-->

* {boolean}

Is `true` if `outgoingMessage.end()` has been called. This property does
not indicate whether the data has been flushed. For that purpose, use
`message.writableFinished` instead.
