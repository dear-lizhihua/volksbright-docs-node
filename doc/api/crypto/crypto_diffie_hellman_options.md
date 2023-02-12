### `crypto.diffieHellman(options)`

<!-- YAML
added:
 - v13.9.0
 - v12.17.0
-->

* `options`: {Object}
  * `privateKey`: {KeyObject}
  * `publicKey`: {KeyObject}
* Returns: {Buffer}

Computes the Diffie-Hellman secret based on a `privateKey` and a `publicKey`.
Both keys must have the same `asymmetricKeyType`, which must be one of `'dh'`
(for Diffie-Hellman), `'ec'` (for ECDH), `'x448'`, or `'x25519'` (for ECDH-ES).
