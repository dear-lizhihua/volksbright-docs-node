### `cipher.final([outputEncoding])`

<!-- YAML
added: v0.1.94
-->

* `outputEncoding` {string} The [encoding][] of the return value.
* Returns: {Buffer | string} Any remaining enciphered contents.
  If `outputEncoding` is specified, a string is
  returned. If an `outputEncoding` is not provided, a [`Buffer`][] is returned.

Once the `cipher.final()` method has been called, the `Cipher` object can no
longer be used to encrypt data. Attempts to call `cipher.final()` more than
once will result in an error being thrown.
