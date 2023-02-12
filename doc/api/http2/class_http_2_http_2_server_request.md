### Class: `http2.Http2ServerRequest`

<!-- YAML
added: v8.4.0
-->

* Extends: {stream.Readable}

A `Http2ServerRequest` object is created by [`http2.Server`][] or
[`http2.SecureServer`][] and passed as the first argument to the
[`'request'`][] event. It may be used to access a request status, headers, and
data.
