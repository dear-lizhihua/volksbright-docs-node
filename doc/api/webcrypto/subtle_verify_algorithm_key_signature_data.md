### `subtle.verify(algorithm, key, signature, data)`

<!-- YAML
added: v15.0.0
changes:
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42507
    description: Added `'Ed25519'`, and `'Ed448'` algorithms.
-->

<!--lint disable maximum-line-length remark-lint-->

* `algorithm`: {AlgorithmIdentifier|RsaPssParams|EcdsaParams|Ed448Params}
* `key`: {CryptoKey}
* `signature`: {ArrayBuffer|TypedArray|DataView|Buffer}
* `data`: {ArrayBuffer|TypedArray|DataView|Buffer}
* Returns: {Promise} containing {boolean}

<!--lint enable maximum-line-length remark-lint-->

Using the method and parameters given in `algorithm` and the keying material
provided by `key`, `subtle.verify()` attempts to verify that `signature` is
a valid cryptographic signature of `data`. The returned promise is resolved
with either `true` or `false`.

The algorithms currently supported include:

* `'RSASSA-PKCS1-v1_5'`
* `'RSA-PSS'`
* `'ECDSA'`
* `'Ed25519'` <span class="experimental-inline"></span>[^1]
* `'Ed448'` <span class="experimental-inline"></span>[^1]
* `'HMAC'`
