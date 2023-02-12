### `crypto.generateKeyPairSync(type, options)`

<!-- YAML
added: v10.12.0
changes:
  - version: v16.10.0
    pr-url: https://github.com/nodejs/node/pull/39927
    description: Add ability to define `RSASSA-PSS-params` sequence parameters
                 for RSA-PSS keys pairs.
  - version:
     - v13.9.0
     - v12.17.0
    pr-url: https://github.com/nodejs/node/pull/31178
    description: Add support for Diffie-Hellman.
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/26960
    description: Add support for RSA-PSS key pairs.
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/26774
    description: Add ability to generate X25519 and X448 key pairs.
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/26554
    description: Add ability to generate Ed25519 and Ed448 key pairs.
  - version: v11.6.0
    pr-url: https://github.com/nodejs/node/pull/24234
    description: The `generateKeyPair` and `generateKeyPairSync` functions now
                 produce key objects if no encoding was specified.
-->

* `type`: {string} Must be `'rsa'`, `'rsa-pss'`, `'dsa'`, `'ec'`, `'ed25519'`,
  `'ed448'`, `'x25519'`, `'x448'`, or `'dh'`.
* `options`: {Object}
  * `modulusLength`: {number} Key size in bits (RSA, DSA).
  * `publicExponent`: {number} Public exponent (RSA). **Default:** `0x10001`.
  * `hashAlgorithm`: {string} Name of the message digest (RSA-PSS).
  * `mgf1HashAlgorithm`: {string} Name of the message digest used by
    MGF1 (RSA-PSS).
  * `saltLength`: {number} Minimal salt length in bytes (RSA-PSS).
  * `divisorLength`: {number} Size of `q` in bits (DSA).
  * `namedCurve`: {string} Name of the curve to use (EC).
  * `prime`: {Buffer} The prime parameter (DH).
  * `primeLength`: {number} Prime length in bits (DH).
  * `generator`: {number} Custom generator (DH). **Default:** `2`.
  * `groupName`: {string} Diffie-Hellman group name (DH). See
    [`crypto.getDiffieHellman()`][].
  * `paramEncoding`: {string} Must be `'named'` or `'explicit'` (EC).
    **Default:** `'named'`.
  * `publicKeyEncoding`: {Object} See [`keyObject.export()`][].
  * `privateKeyEncoding`: {Object} See [`keyObject.export()`][].
* Returns: {Object}
  * `publicKey`: {string | Buffer | KeyObject}
  * `privateKey`: {string | Buffer | KeyObject}

Generates a new asymmetric key pair of the given `type`. RSA, RSA-PSS, DSA, EC,
Ed25519, Ed448, X25519, X448, and DH are currently supported.

If a `publicKeyEncoding` or `privateKeyEncoding` was specified, this function
behaves as if [`keyObject.export()`][] had been called on its result. Otherwise,
the respective part of the key is returned as a [`KeyObject`][].

When encoding public keys, it is recommended to use `'spki'`. When encoding
private keys, it is recommended to use `'pkcs8'` with a strong passphrase,
and to keep the passphrase confidential.

```mjs
const {
  generateKeyPairSync,
} = await import('node:crypto');

const {
  publicKey,
  privateKey,
} = generateKeyPairSync('rsa', {
  modulusLength: 4096,
  publicKeyEncoding: {
    type: 'spki',
    format: 'pem',
  },
  privateKeyEncoding: {
    type: 'pkcs8',
    format: 'pem',
    cipher: 'aes-256-cbc',
    passphrase: 'top secret',
  },
});
```

```cjs
const {
  generateKeyPairSync,
} = require('node:crypto');

const {
  publicKey,
  privateKey,
} = generateKeyPairSync('rsa', {
  modulusLength: 4096,
  publicKeyEncoding: {
    type: 'spki',
    format: 'pem',
  },
  privateKeyEncoding: {
    type: 'pkcs8',
    format: 'pem',
    cipher: 'aes-256-cbc',
    passphrase: 'top secret',
  },
});
```

The return value `{ publicKey, privateKey }` represents the generated key pair.
When PEM encoding was selected, the respective key will be a string, otherwise
it will be a buffer containing the data encoded as DER.
