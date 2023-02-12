### `verify.verify(object, signature[, signatureEncoding])`

<!-- YAML
added: v0.1.92
changes:
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/35093
    description: The object can also be an ArrayBuffer and CryptoKey.
  - version:
     - v13.2.0
     - v12.16.0
    pr-url: https://github.com/nodejs/node/pull/29292
    description: This function now supports IEEE-P1363 DSA and ECDSA signatures.
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/26960
    description: This function now supports RSA-PSS keys.
  - version: v11.7.0
    pr-url: https://github.com/nodejs/node/pull/25217
    description: The key can now be a private key.
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/11705
    description: Support for RSASSA-PSS and additional options was added.
-->

<!--lint disable maximum-line-length remark-lint-->

* `object` {Object|string|ArrayBuffer|Buffer|TypedArray|DataView|KeyObject|CryptoKey}
  * `dsaEncoding` {string}
  * `padding` {integer}
  * `saltLength` {integer}
* `signature` {string|ArrayBuffer|Buffer|TypedArray|DataView}
* `signatureEncoding` {string} The [encoding][] of the `signature` string.
* Returns: {boolean} `true` or `false` depending on the validity of the
  signature for the data and public key.

<!--lint enable maximum-line-length remark-lint-->

Verifies the provided data using the given `object` and `signature`.

If `object` is not a [`KeyObject`][], this function behaves as if
`object` had been passed to [`crypto.createPublicKey()`][]. If it is an
object, the following additional properties can be passed:

* `dsaEncoding` {string} For DSA and ECDSA, this option specifies the
  format of the signature. It can be one of the following:
  * `'der'` (default): DER-encoded ASN.1 signature structure encoding `(r, s)`.
  * `'ieee-p1363'`: Signature format `r || s` as proposed in IEEE-P1363.
* `padding` {integer} Optional padding value for RSA, one of the following:

  * `crypto.constants.RSA_PKCS1_PADDING` (default)
  * `crypto.constants.RSA_PKCS1_PSS_PADDING`

  `RSA_PKCS1_PSS_PADDING` will use MGF1 with the same hash function
  used to verify the message as specified in section 3.1 of [RFC 4055][], unless
  an MGF1 hash function has been specified as part of the key in compliance with
  section 3.3 of [RFC 4055][].
* `saltLength` {integer} Salt length for when padding is
  `RSA_PKCS1_PSS_PADDING`. The special value
  `crypto.constants.RSA_PSS_SALTLEN_DIGEST` sets the salt length to the digest
  size, `crypto.constants.RSA_PSS_SALTLEN_AUTO` (default) causes it to be
  determined automatically.

The `signature` argument is the previously calculated signature for the data, in
the `signatureEncoding`.
If a `signatureEncoding` is specified, the `signature` is expected to be a
string; otherwise `signature` is expected to be a [`Buffer`][],
`TypedArray`, or `DataView`.

The `verify` object can not be used again after `verify.verify()` has been
called. Multiple calls to `verify.verify()` will result in an error being
thrown.

Because public keys can be derived from private keys, a private key may
be passed instead of a public key.
