### `http2.getUnpackedSettings(buf)`

<!-- YAML
added: v8.4.0
-->

* `buf` {Buffer|TypedArray} The packed settings.
* Returns: {HTTP/2 Settings Object}

Returns a [HTTP/2 Settings Object][] containing the deserialized settings from
the given `Buffer` as generated by `http2.getPackedSettings()`.
