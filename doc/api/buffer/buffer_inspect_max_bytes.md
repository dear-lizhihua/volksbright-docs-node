### `buffer.INSPECT_MAX_BYTES`

<!-- YAML
added: v0.5.4
-->

* {integer} **Default:** `50`

Returns the maximum number of bytes that will be returned when
`buf.inspect()` is called. This can be overridden by user modules. See
[`util.inspect()`][] for more details on `buf.inspect()` behavior.
