### `cryptoKey.usages`

<!-- YAML
added: v15.0.0
-->

* Type: {string\[]}

An array of strings identifying the operations for which the
key may be used.

The possible usages are:

* `'encrypt'` - The key may be used to encrypt data.
* `'decrypt'` - The key may be used to decrypt data.
* `'sign'` - The key may be used to generate digital signatures.
* `'verify'` - The key may be used to verify digital signatures.
* `'deriveKey'` - The key may be used to derive a new key.
* `'deriveBits'` - The key may be used to derive bits.
* `'wrapKey'` - The key may be used to wrap another key.
* `'unwrapKey'` - The key may be used to unwrap another key.

Valid key usages depend on the key algorithm (identified by
`cryptokey.algorithm.name`).

| Key Type                                                  | `'encrypt'` | `'decrypt'` | `'sign'` | `'verify'` | `'deriveKey'` | `'deriveBits'` | `'wrapKey'` | `'unwrapKey'` |
| --------------------------------------------------------- | ----------- | ----------- | -------- | ---------- | ------------- | -------------- | ----------- | ------------- |
| `'AES-CBC'`                                               | ✔           | ✔           |          |            |               |                | ✔           | ✔             |
| `'AES-CTR'`                                               | ✔           | ✔           |          |            |               |                | ✔           | ✔             |
| `'AES-GCM'`                                               | ✔           | ✔           |          |            |               |                | ✔           | ✔             |
| `'AES-KW'`                                                |             |             |          |            |               |                | ✔           | ✔             |
| `'ECDH'`                                                  |             |             |          |            | ✔             | ✔              |             |               |
| `'X25519'` <span class="experimental-inline"></span>[^1]  |             |             |          |            | ✔             | ✔              |             |               |
| `'X448'` <span class="experimental-inline"></span>[^1]    |             |             |          |            | ✔             | ✔              |             |               |
| `'ECDSA'`                                                 |             |             | ✔        | ✔          |               |                |             |               |
| `'Ed25519'` <span class="experimental-inline"></span>[^1] |             |             | ✔        | ✔          |               |                |             |               |
| `'Ed448'` <span class="experimental-inline"></span>[^1]   |             |             | ✔        | ✔          |               |                |             |               |
| `'HDKF'`                                                  |             |             |          |            | ✔             | ✔              |             |               |
| `'HMAC'`                                                  |             |             | ✔        | ✔          |               |                |             |               |
| `'PBKDF2'`                                                |             |             |          |            | ✔             | ✔              |             |               |
| `'RSA-OAEP'`                                              | ✔           | ✔           |          |            |               |                | ✔           | ✔             |
| `'RSA-PSS'`                                               |             |             | ✔        | ✔          |               |                |             |               |
| `'RSASSA-PKCS1-v1_5'`                                     |             |             | ✔        | ✔          |               |                |             |               |
