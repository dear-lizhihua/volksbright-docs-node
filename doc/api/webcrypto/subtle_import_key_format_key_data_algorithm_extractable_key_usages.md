### `subtle.importKey(format, keyData, algorithm, extractable, keyUsages)`

<!-- YAML
added: v15.0.0
changes:
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42507
    description: Added `'Ed25519'`, `'Ed448'`, `'X25519'`, and `'X448'`
      algorithms.
  - version: v15.9.0
    pr-url: https://github.com/nodejs/node/pull/37203
    description: Removed `'NODE-DSA'` JWK import.
-->

* `format`: {string} Must be one of `'raw'`, `'pkcs8'`, `'spki'`, or `'jwk'`.
* `keyData`: {ArrayBuffer|TypedArray|DataView|Buffer|Object}

<!--lint disable maximum-line-length remark-lint-->

* `algorithm`: {AlgorithmIdentifier|RsaHashedImportParams|EcKeyImportParams|HmacImportParams}

<!--lint enable maximum-line-length remark-lint-->

* `extractable`: {boolean}
* `keyUsages`: {string\[]} See [Key usages][].
* Returns: {Promise} containing {CryptoKey}

The `subtle.importKey()` method attempts to interpret the provided `keyData`
as the given `format` to create a {CryptoKey} instance using the provided
`algorithm`, `extractable`, and `keyUsages` arguments. If the import is
successful, the returned promise will be resolved with the created {CryptoKey}.

If importing a `'PBKDF2'` key, `extractable` must be `false`.

The algorithms currently supported include:

| Key Type                                                  | `'spki'` | `'pkcs8'` | `'jwk'` | `'raw'` |
| --------------------------------------------------------- | -------- | --------- | ------- | ------- |
| `'AES-CBC'`                                               |          |           | ✔       | ✔       |
| `'AES-CTR'`                                               |          |           | ✔       | ✔       |
| `'AES-GCM'`                                               |          |           | ✔       | ✔       |
| `'AES-KW'`                                                |          |           | ✔       | ✔       |
| `'ECDH'`                                                  | ✔        | ✔         | ✔       | ✔       |
| `'X25519'` <span class="experimental-inline"></span>[^1]  | ✔        | ✔         | ✔       | ✔       |
| `'X448'` <span class="experimental-inline"></span>[^1]    | ✔        | ✔         | ✔       | ✔       |
| `'ECDSA'`                                                 | ✔        | ✔         | ✔       | ✔       |
| `'Ed25519'` <span class="experimental-inline"></span>[^1] | ✔        | ✔         | ✔       | ✔       |
| `'Ed448'` <span class="experimental-inline"></span>[^1]   | ✔        | ✔         | ✔       | ✔       |
| `'HDKF'`                                                  |          |           |         | ✔       |
| `'HMAC'`                                                  |          |           | ✔       | ✔       |
| `'PBKDF2'`                                                |          |           |         | ✔       |
| `'RSA-OAEP'`                                              | ✔        | ✔         | ✔       |         |
| `'RSA-PSS'`                                               | ✔        | ✔         | ✔       |         |
| `'RSASSA-PKCS1-v1_5'`                                     | ✔        | ✔         | ✔       |         |
