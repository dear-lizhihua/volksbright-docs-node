#### Event: `'request'`

<!-- YAML
added: v8.4.0
-->

* `request` {http2.Http2ServerRequest}
* `response` {http2.Http2ServerResponse}

Emitted each time there is a request. There may be multiple requests
per session. See the [Compatibility API][].
