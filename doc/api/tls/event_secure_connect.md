### Event: `'secureConnect'`

<!-- YAML
added: v0.11.4
-->

The `'secureConnect'` event is emitted after the handshaking process for a new
connection has successfully completed. The listener callback will be called
regardless of whether or not the server's certificate has been authorized. It
is the client's responsibility to check the `tlsSocket.authorized` property to
determine if the server certificate was signed by one of the specified CAs. If
`tlsSocket.authorized === false`, then the error can be found by examining the
`tlsSocket.authorizationError` property. If ALPN was used, the
`tlsSocket.alpnProtocol` property can be checked to determine the negotiated
protocol.

The `'secureConnect'` event is not emitted when a {tls.TLSSocket} is created
using the `new tls.TLSSocket()` constructor.
