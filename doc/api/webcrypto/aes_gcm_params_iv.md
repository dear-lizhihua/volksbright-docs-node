#### `aesGcmParams.iv`

<!-- YAML
added: v15.0.0
-->

* Type: {ArrayBuffer|TypedArray|DataView|Buffer}

The initialization vector must be unique for every encryption operation using a
given key.

Ideally, this is a deterministic 12-byte value that is computed in such a way
that it is guaranteed to be unique across all invocations that use the same key.
Alternatively, the initialization vector may consist of at least 12
cryptographically random bytes. For more information on constructing
initialization vectors for AES-GCM, refer to Section 8 of [NIST SP 800-38D][].
