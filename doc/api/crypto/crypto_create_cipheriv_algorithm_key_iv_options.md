### `crypto.createCipheriv(algorithm, key, iv[, options])`

<!-- YAML
added: v0.1.94
changes:
  - version:
    - v17.9.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42427
    description: The `authTagLength` option is now optional when using the
                 `chacha20-poly1305` cipher and defaults to 16 bytes.
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/35093
    description: The password and iv arguments can be an ArrayBuffer and are
                 each limited to a maximum of 2 ** 31 - 1 bytes.
  - version: v11.6.0
    pr-url: https://github.com/nodejs/node/pull/24234
    description: The `key` argument can now be a `KeyObject`.
  - version:
     - v11.2.0
     - v10.17.0
    pr-url: https://github.com/nodejs/node/pull/24081
    description: The cipher `chacha20-poly1305` (the IETF variant of
                 ChaCha20-Poly1305) is now supported.
  - version: v10.10.0
    pr-url: https://github.com/nodejs/node/pull/21447
    description: Ciphers in OCB mode are now supported.
  - version: v10.2.0
    pr-url: https://github.com/nodejs/node/pull/20235
    description: The `authTagLength` option can now be used to produce shorter
                 authentication tags in GCM mode and defaults to 16 bytes.
  - version: v9.9.0
    pr-url: https://github.com/nodejs/node/pull/18644
    description: The `iv` parameter may now be `null` for ciphers which do not
                 need an initialization vector.
-->

* `algorithm` {string}
* `key` {string|ArrayBuffer|Buffer|TypedArray|DataView|KeyObject|CryptoKey}
* `iv` {string|ArrayBuffer|Buffer|TypedArray|DataView|null}
* `options` {Object} [`stream.transform` options][]
* Returns: {Cipher}

Creates and returns a `Cipher` object, with the given `algorithm`, `key` and
initialization vector (`iv`).

The `options` argument controls stream behavior and is optional except when a
cipher in CCM or OCB mode (e.g. `'aes-128-ccm'`) is used. In that case, the
`authTagLength` option is required and specifies the length of the
authentication tag in bytes, see [CCM mode][]. In GCM mode, the `authTagLength`
option is not required but can be used to set the length of the authentication
tag that will be returned by `getAuthTag()` and defaults to 16 bytes.
For `chacha20-poly1305`, the `authTagLength` option defaults to 16 bytes.

The `algorithm` is dependent on OpenSSL, examples are `'aes192'`, etc. On
recent OpenSSL releases, `openssl list -cipher-algorithms` will
display the available cipher algorithms.

The `key` is the raw key used by the `algorithm` and `iv` is an
[initialization vector][]. Both arguments must be `'utf8'` encoded strings,
[Buffers][`Buffer`], `TypedArray`, or `DataView`s. The `key` may optionally be
a [`KeyObject`][] of type `secret`. If the cipher does not need
an initialization vector, `iv` may be `null`.

When passing strings for `key` or `iv`, please consider
[caveats when using strings as inputs to cryptographic APIs][].

Initialization vectors should be unpredictable and unique; ideally, they will be
cryptographically random. They do not have to be secret: IVs are typically just
added to ciphertext messages unencrypted. It may sound contradictory that
something has to be unpredictable and unique, but does not have to be secret;
remember that an attacker must not be able to predict ahead of time what a
given IV will be.
