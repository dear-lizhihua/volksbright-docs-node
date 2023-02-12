### `subtle.deriveKey(algorithm, baseKey, derivedKeyAlgorithm, extractable, keyUsages)`

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
* `derivedKeyAlgorithm`: {HmacKeyGenParams|AesKeyGenParams}
* `extractable`: {boolean}
* `keyUsages`: {string\[]} See [Key usages][].
* Returns: {Promise} containing {CryptoKey}

<!--lint enable maximum-line-length remark-lint-->

Using the method and parameters specified in `algorithm`, and the keying
material provided by `baseKey`, `subtle.deriveKey()` attempts to generate
a new {CryptoKey} based on the method and parameters in `derivedKeyAlgorithm`.

Calling `subtle.deriveKey()` is equivalent to calling `subtle.deriveBits()` to
generate raw keying material, then passing the result into the
`subtle.importKey()` method using the `deriveKeyAlgorithm`, `extractable`, and
`keyUsages` parameters as input.

The algorithms currently supported include:

* `'ECDH'`
* `'X25519'` <span class="experimental-inline"></span>[^1]
* `'X448'` <span class="experimental-inline"></span>[^1]
* `'HKDF'`
* `'PBKDF2'`
