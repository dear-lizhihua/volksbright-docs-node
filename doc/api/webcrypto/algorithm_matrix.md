## Algorithm matrix

The table details the algorithms supported by the Node.js Web Crypto API
implementation and the APIs supported for each:

| Algorithm                                                 | `generateKey` | `exportKey` | `importKey` | `encrypt` | `decrypt` | `wrapKey` | `unwrapKey` | `deriveBits` | `deriveKey` | `sign` | `verify` | `digest` |
| --------------------------------------------------------- | ------------- | ----------- | ----------- | --------- | --------- | --------- | ----------- | ------------ | ----------- | ------ | -------- | -------- |
| `'RSASSA-PKCS1-v1_5'`                                     | ✔             | ✔           | ✔           |           |           |           |             |              |             | ✔      | ✔        |          |
| `'RSA-PSS'`                                               | ✔             | ✔           | ✔           |           |           |           |             |              |             | ✔      | ✔        |          |
| `'RSA-OAEP'`                                              | ✔             | ✔           | ✔           | ✔         | ✔         | ✔         | ✔           |              |             |        |          |          |
| `'ECDSA'`                                                 | ✔             | ✔           | ✔           |           |           |           |             |              |             | ✔      | ✔        |          |
| `'Ed25519'` <span class="experimental-inline"></span>[^1] | ✔             | ✔           | ✔           |           |           |           |             |              |             | ✔      | ✔        |          |
| `'Ed448'` <span class="experimental-inline"></span>[^1]   | ✔             | ✔           | ✔           |           |           |           |             |              |             | ✔      | ✔        |          |
| `'ECDH'`                                                  | ✔             | ✔           | ✔           |           |           |           |             | ✔            | ✔           |        |          |          |
| `'X25519'` <span class="experimental-inline"></span>[^1]  | ✔             | ✔           | ✔           |           |           |           |             | ✔            | ✔           |        |          |          |
| `'X448'` <span class="experimental-inline"></span>[^1]    | ✔             | ✔           | ✔           |           |           |           |             | ✔            | ✔           |        |          |          |
| `'AES-CTR'`                                               | ✔             | ✔           | ✔           | ✔         | ✔         | ✔         | ✔           |              |             |        |          |          |
| `'AES-CBC'`                                               | ✔             | ✔           | ✔           | ✔         | ✔         | ✔         | ✔           |              |             |        |          |          |
| `'AES-GCM'`                                               | ✔             | ✔           | ✔           | ✔         | ✔         | ✔         | ✔           |              |             |        |          |          |
| `'AES-KW'`                                                | ✔             | ✔           | ✔           |           |           | ✔         | ✔           |              |             |        |          |          |
| `'HMAC'`                                                  | ✔             | ✔           | ✔           |           |           |           |             |              |             | ✔      | ✔        |          |
| `'HKDF'`                                                  |               | ✔           | ✔           |           |           |           |             | ✔            | ✔           |        |          |          |
| `'PBKDF2'`                                                |               | ✔           | ✔           |           |           |           |             | ✔            | ✔           |        |          |          |
| `'SHA-1'`                                                 |               |             |             |           |           |           |             |              |             |        |          | ✔        |
| `'SHA-256'`                                               |               |             |             |           |           |           |             |              |             |        |          | ✔        |
| `'SHA-384'`                                               |               |             |             |           |           |           |             |              |             |        |          | ✔        |
| `'SHA-512'`                                               |               |             |             |           |           |           |             |              |             |        |          | ✔        |
