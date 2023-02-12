### `crypto.createDecipher(algorithm, password[, options])`

<!-- YAML
added: v0.1.94
deprecated: v10.0.0
changes:
  - version:
    - v17.9.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42427
    description: The `authTagLength` option is now optional when using the
                 `chacha20-poly1305` cipher and defaults to 16 bytes.
  - version: v10.10.0
    pr-url: https://github.com/nodejs/node/pull/21447
    description: Ciphers in OCB mode are now supported.
-->

> Stability: 0 - Deprecated: Use [`crypto.createDecipheriv()`][] instead.

* `algorithm` {string}
* `password` {string|ArrayBuffer|Buffer|TypedArray|DataView}
* `options` {Object} [`stream.transform` options][]
* Returns: {Decipher}

Creates and returns a `Decipher` object that uses the given `algorithm` and
`password` (key).

The `options` argument controls stream behavior and is optional except when a
cipher in CCM or OCB mode (e.g. `'aes-128-ccm'`) is used. In that case, the
`authTagLength` option is required and specifies the length of the
authentication tag in bytes, see [CCM mode][].
For `chacha20-poly1305`, the `authTagLength` option defaults to 16 bytes.

<strong class="critical">This function is semantically insecure for all
supported ciphers and fatally flawed for ciphers in counter mode (such as CTR,
GCM, or CCM).</strong>

The implementation of `crypto.createDecipher()` derives keys using the OpenSSL
function [`EVP_BytesToKey`][] with the digest algorithm set to MD5, one
iteration, and no salt. The lack of salt allows dictionary attacks as the same
password always creates the same key. The low iteration count and
non-cryptographically secure hash algorithm allow passwords to be tested very
rapidly.

In line with OpenSSL's recommendation to use a more modern algorithm instead of
[`EVP_BytesToKey`][] it is recommended that developers derive a key and IV on
their own using [`crypto.scrypt()`][] and to use [`crypto.createDecipheriv()`][]
to create the `Decipher` object.
