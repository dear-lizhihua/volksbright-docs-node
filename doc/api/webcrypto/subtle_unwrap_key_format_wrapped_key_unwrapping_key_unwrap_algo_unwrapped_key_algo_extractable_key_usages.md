### `subtle.unwrapKey(format, wrappedKey, unwrappingKey, unwrapAlgo, unwrappedKeyAlgo, extractable, keyUsages)`

<!-- YAML
added: v15.0.0
-->

* `format`: {string} Must be one of `'raw'`, `'pkcs8'`, `'spki'`, or `'jwk'`.
* `wrappedKey`: {ArrayBuffer|TypedArray|DataView|Buffer}
* `unwrappingKey`: {CryptoKey}

<!--lint disable maximum-line-length remark-lint-->

* `unwrapAlgo`: {AlgorithmIdentifier|RsaOaepParams|AesCtrParams|AesCbcParams|AesGcmParams}
* `unwrappedKeyAlgo`: {AlgorithmIdentifier|RsaHashedImportParams|EcKeyImportParams|HmacImportParams}

<!--lint enable maximum-line-length remark-lint-->

* `extractable`: {boolean}
* `keyUsages`: {string\[]} See [Key usages][].
* Returns: {Promise} containing {CryptoKey}

In cryptography, "wrapping a key" refers to exporting and then encrypting the
keying material. The `subtle.unwrapKey()` method attempts to decrypt a wrapped
key and create a {CryptoKey} instance. It is equivalent to calling
`subtle.decrypt()` first on the encrypted key data (using the `wrappedKey`,
`unwrapAlgo`, and `unwrappingKey` arguments as input) then passing the results
in to the `subtle.importKey()` method using the `unwrappedKeyAlgo`,
`extractable`, and `keyUsages` arguments as inputs. If successful, the returned
promise is resolved with a {CryptoKey} object.

The wrapping algorithms currently supported include:

* `'RSA-OAEP'`
* `'AES-CTR'`
* `'AES-CBC'`
* `'AES-GCM'`
* `'AES-KW'`

The unwrapped key algorithms supported include:

* `'RSASSA-PKCS1-v1_5'`
* `'RSA-PSS'`
* `'RSA-OAEP'`
* `'ECDSA'`
* `'Ed25519'` <span class="experimental-inline"></span>[^1]
* `'Ed448'` <span class="experimental-inline"></span>[^1]
* `'ECDH'`
* `'X25519'` <span class="experimental-inline"></span>[^1]
* `'X448'` <span class="experimental-inline"></span>[^1]
* `'HMAC'`
* `'AES-CTR'`
* `'AES-CBC'`
* `'AES-GCM'`
* `'AES-KW'`
