### Class: `Http2Session`

<!-- YAML
added: v8.4.0
-->

* Extends: {EventEmitter}

Instances of the `http2.Http2Session` class represent an active communications
session between an HTTP/2 client and server. Instances of this class are _not_
intended to be constructed directly by user code.

Each `Http2Session` instance will exhibit slightly different behaviors
depending on whether it is operating as a server or a client. The
`http2session.type` property can be used to determine the mode in which an
`Http2Session` is operating. On the server side, user code should rarely
have occasion to work with the `Http2Session` object directly, with most
actions typically taken through interactions with either the `Http2Server` or
`Http2Stream` objects.

User code will not create `Http2Session` instances directly. Server-side
`Http2Session` instances are created by the `Http2Server` instance when a
new HTTP/2 connection is received. Client-side `Http2Session` instances are
created using the `http2.connect()` method.
