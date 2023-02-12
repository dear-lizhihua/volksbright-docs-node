### `crypto.createSecretKey(key[, encoding])`

<!-- YAML
added: v11.6.0
changes:
  - version:
    - v18.8.0
    - v16.18.0
    pr-url: https://github.com/nodejs/node/pull/44201
    description: The key can now be zero-length.
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/35093
    description: The key can also be an ArrayBuffer or string. The encoding
                 argument was added. The key cannot contain more than
                 2 ** 32 - 1 bytes.
-->

* `key` {string|ArrayBuffer|Buffer|TypedArray|DataView}
* `encoding` {string} The string encoding when `key` is a string.
* Returns: {KeyObject}

Creates and returns a new key object containing a secret key for symmetric
encryption or `Hmac`.
