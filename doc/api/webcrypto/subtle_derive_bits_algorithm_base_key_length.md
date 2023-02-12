### `subtle.deriveBits(algorithm, baseKey, length)`

<!-- YAML
added: v15.0.0
changes:
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42507
    description: Added `'X25519'`, and `'X448'` algorithms.
-->

<!--lint disable maximum-line-length remark-lint-->

* `algorithm`: {AlgorithmIdentifier|EcdhKeyDeriveParams|HkdfParams|Pbkdf2Params}
* `baseKey`: {CryptoKey}
* `length`: {number|null}
* Returns: {Promise} containing {ArrayBuffer}

<!--lint enable maximum-line-length remark-lint-->

Using the method and parameters specified in `algorithm` and the keying
material provided by `baseKey`, `subtle.deriveBits()` attempts to generate
`length` bits.

The Node.js implementation requires that when `length` is a
number it must be multiple of `8`.

When `length` is `null` the maximum number of bits for a given algorithm is
generated. This is allowed for the `'ECDH'`, `'X25519'`, and `'X448'`
algorithms.

If successful, the returned promise will be resolved with an {ArrayBuffer}
containing the generated data.

The algorithms currently supported include:

* `'ECDH'`
* `'X25519'` <span class="experimental-inline"></span>[^1]
* `'X448'` <span class="experimental-inline"></span>[^1]
* `'HKDF'`
* `'PBKDF2'`
