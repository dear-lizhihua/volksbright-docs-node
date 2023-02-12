### `subtle.exportKey(format, key)`

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
    description: Removed `'NODE-DSA'` JWK export.
-->

* `format`: {string} Must be one of `'raw'`, `'pkcs8'`, `'spki'`, or `'jwk'`.
* `key`: {CryptoKey}
* Returns: {Promise} containing {ArrayBuffer|Object}.

Exports the given key into the specified format, if supported.

If the {CryptoKey} is not extractable, the returned promise will reject.

When `format` is either `'pkcs8'` or `'spki'` and the export is successful,
the returned promise will be resolved with an {ArrayBuffer} containing the
exported key data.

When `format` is `'jwk'` and the export is successful, the returned promise
will be resolved with a JavaScript object conforming to the [JSON Web Key][]
specification.

| Key Type                                                  | `'spki'` | `'pkcs8'` | `'jwk'` | `'raw'` |
| --------------------------------------------------------- | -------- | --------- | ------- | ------- |
| `'AES-CBC'`                                               |          |           | ✔       | ✔       |
| `'AES-CTR'`                                               |          |           | ✔       | ✔       |
| `'AES-GCM'`                                               |          |           | ✔       | ✔       |
| `'AES-KW'`                                                |          |           | ✔       | ✔       |
| `'ECDH'`                                                  | ✔        | ✔         | ✔       | ✔       |
| `'ECDSA'`                                                 | ✔        | ✔         | ✔       | ✔       |
| `'Ed25519'` <span class="experimental-inline"></span>[^1] | ✔        | ✔         | ✔       | ✔       |
| `'Ed448'` <span class="experimental-inline"></span>[^1]   | ✔        | ✔         | ✔       | ✔       |
| `'HDKF'`                                                  |          |           |         |         |
| `'HMAC'`                                                  |          |           | ✔       | ✔       |
| `'PBKDF2'`                                                |          |           |         |         |
| `'RSA-OAEP'`                                              | ✔        | ✔         | ✔       |         |
| `'RSA-PSS'`                                               | ✔        | ✔         | ✔       |         |
| `'RSASSA-PKCS1-v1_5'`                                     | ✔        | ✔         | ✔       |         |
