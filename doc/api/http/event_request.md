### Event: `'request'`

<!-- YAML
added: v0.1.0
-->

* `request` {http.IncomingMessage}
* `response` {http.ServerResponse}

Emitted each time there is a request. There may be multiple requests
per connection (in the case of HTTP Keep-Alive connections).
