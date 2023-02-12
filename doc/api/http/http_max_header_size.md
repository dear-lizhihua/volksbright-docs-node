## `http.maxHeaderSize`

<!-- YAML
added:
 - v11.6.0
 - v10.15.0
-->

* {number}

Read-only property specifying the maximum allowed size of HTTP headers in bytes.
Defaults to 16 KiB. Configurable using the [`--max-http-header-size`][] CLI
option.

This can be overridden for servers and client requests by passing the
`maxHeaderSize` option.
