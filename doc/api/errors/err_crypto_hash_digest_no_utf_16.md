### `ERR_CRYPTO_HASH_DIGEST_NO_UTF16`

<!-- YAML
added: v9.0.0
removed: v12.12.0
-->

The UTF-16 encoding was used with [`hash.digest()`][]. While the
`hash.digest()` method does allow an `encoding` argument to be passed in,
causing the method to return a string rather than a `Buffer`, the UTF-16
encoding (e.g. `ucs` or `utf16le`) is not supported.

<a id="ERR_HTTP2_FRAME_ERROR"></a>
