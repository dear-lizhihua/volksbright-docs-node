### `subtle.generateKey(algorithm, extractable, keyUsages)`

<!-- YAML
added: v15.0.0
-->

<!--lint disable maximum-line-length remark-lint-->

* `algorithm`: {AlgorithmIdentifier|RsaHashedKeyGenParams|EcKeyGenParams|HmacKeyGenParams|AesKeyGenParams}

<!--lint enable maximum-line-length remark-lint-->

* `extractable`: {boolean}
* `keyUsages`: {string\[]} See [Key usages][].
* Returns: {Promise} containing {CryptoKey|CryptoKeyPair}

Using the method and parameters provided in `algorithm`, `subtle.generateKey()`
attempts to generate new keying material. Depending the method used, the method
may generate either a single {CryptoKey} or a {CryptoKeyPair}.

The {CryptoKeyPair} (public and private key) generating algorithms supported
include:

* `'RSASSA-PKCS1-v1_5'`
* `'RSA-PSS'`
* `'RSA-OAEP'`
* `'ECDSA'`
* `'Ed25519'` <span class="experimental-inline"></span>[^1]
* `'Ed448'` <span class="experimental-inline"></span>[^1]
* `'ECDH'`
* `'X25519'` <span class="experimental-inline"></span>[^1]
* `'X448'` <span class="experimental-inline"></span>[^1]

The {CryptoKey} (secret key) generating algorithms supported include:

* `'HMAC'`
* `'AES-CTR'`
* `'AES-CBC'`
* `'AES-GCM'`
* `'AES-KW'`
