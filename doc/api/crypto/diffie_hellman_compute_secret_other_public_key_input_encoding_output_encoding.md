### `diffieHellman.computeSecret(otherPublicKey[, inputEncoding][, outputEncoding])`

<!-- YAML
added: v0.5.0
-->

* `otherPublicKey` {string|ArrayBuffer|Buffer|TypedArray|DataView}
* `inputEncoding` {string} The [encoding][] of an `otherPublicKey` string.
* `outputEncoding` {string} The [encoding][] of the return value.
* Returns: {Buffer | string}

Computes the shared secret using `otherPublicKey` as the other
party's public key and returns the computed shared secret. The supplied
key is interpreted using the specified `inputEncoding`, and secret is
encoded using specified `outputEncoding`.
If the `inputEncoding` is not
provided, `otherPublicKey` is expected to be a [`Buffer`][],
`TypedArray`, or `DataView`.

If `outputEncoding` is given a string is returned; otherwise, a
[`Buffer`][] is returned.
