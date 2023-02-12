## Core API

The Core API provides a low-level interface designed specifically around
support for HTTP/2 protocol features. It is specifically _not_ designed for
compatibility with the existing [HTTP/1][] module API. However,
the [Compatibility API][] is.

The `http2` Core API is much more symmetric between client and server than the
`http` API. For instance, most events, like `'error'`, `'connect'` and
`'stream'`, can be emitted either by client-side code or server-side code.
