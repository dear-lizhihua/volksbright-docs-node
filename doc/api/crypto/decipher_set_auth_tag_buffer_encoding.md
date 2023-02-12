### `decipher.setAuthTag(buffer[, encoding])`

<!-- YAML
added: v1.0.0
changes:
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/35093
    description: The buffer argument can be a string or ArrayBuffer and is
                limited to no more than 2 ** 31 - 1 bytes.
  - version: v11.0.0
    pr-url: https://github.com/nodejs/node/pull/17825
    description: This method now throws if the GCM tag length is invalid.
  - version: v7.2.0
    pr-url: https://github.com/nodejs/node/pull/9398
    description: This method now returns a reference to `decipher`.
-->

* `buffer` {string|Buffer|ArrayBuffer|TypedArray|DataView}
* `encoding` {string} String encoding to use when `buffer` is a string.
* Returns: {Decipher} for method chaining.

When using an authenticated encryption mode (`GCM`, `CCM`, `OCB`, and
`chacha20-poly1305` are
currently supported), the `decipher.setAuthTag()` method is used to pass in the
received _authentication tag_. If no tag is provided, or if the cipher text
has been tampered with, [`decipher.final()`][] will throw, indicating that the
cipher text should be discarded due to failed authentication. If the tag length
is invalid according to [NIST SP 800-38D][] or does not match the value of the
`authTagLength` option, `decipher.setAuthTag()` will throw an error.

The `decipher.setAuthTag()` method must be called before [`decipher.update()`][]
for `CCM` mode or before [`decipher.final()`][] for `GCM` and `OCB` modes and
`chacha20-poly1305`.
`decipher.setAuthTag()` can only be called once.

When passing a string as the authentication tag, please consider
[caveats when using strings as inputs to cryptographic APIs][].
