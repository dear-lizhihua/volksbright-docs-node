### `cipher.getAuthTag()`

<!-- YAML
added: v1.0.0
-->

* Returns: {Buffer} When using an authenticated encryption mode (`GCM`, `CCM`,
  `OCB`, and `chacha20-poly1305` are currently supported), the
  `cipher.getAuthTag()` method returns a
  [`Buffer`][] containing the _authentication tag_ that has been computed from
  the given data.

The `cipher.getAuthTag()` method should only be called after encryption has
been completed using the [`cipher.final()`][] method.

If the `authTagLength` option was set during the `cipher` instance's creation,
this function will return exactly `authTagLength` bytes.
