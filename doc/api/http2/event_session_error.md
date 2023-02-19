#### Event: `'sessionError'`

<!-- YAML
added: v8.4.0
-->

* `error` {Error}
* `session` {ServerHttp2Session}

The `'sessionError'` event is emitted when an `'error'` event is emitted by
an `Http2Session` object associated with the `Http2Server`.
