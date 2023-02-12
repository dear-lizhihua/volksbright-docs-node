#### Event: `'unknownProtocol'`

<!-- YAML
added: v8.4.0
changes:
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/44031
    description: This event will only be emitted if the client did not transmit
                 an ALPN extension during the TLS handshake.
-->

* `socket` {stream.Duplex}

The `'unknownProtocol'` event is emitted when a connecting client fails to
negotiate an allowed protocol (i.e. HTTP/2 or HTTP/1.1). The event handler
receives the socket for handling. If no listener is registered for this event,
the connection is terminated. A timeout may be specified using the
`'unknownProtocolTimeout'` option passed to [`http2.createSecureServer()`][].

In earlier versions of Node.js, this event would be emitted if `allowHTTP1` is
`false` and, during the TLS handshake, the client either does not send an ALPN
extension or sends an ALPN extension that does not include HTTP/2 (`h2`). Newer
versions of Node.js only emit this event if `allowHTTP1` is `false` and the
client does not send an ALPN extension. If the client sends an ALPN extension
that does not include HTTP/2 (or HTTP/1.1 if `allowHTTP1` is `true`), the TLS
handshake will fail and no secure connection will be established.

See the [Compatibility API][].
