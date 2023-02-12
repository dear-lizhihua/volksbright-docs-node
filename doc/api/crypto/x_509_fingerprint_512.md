### `x509.fingerprint512`

<!-- YAML
added:
  - v17.2.0
  - v16.14.0
-->

* Type: {string}

The SHA-512 fingerprint of this certificate.

Because computing the SHA-256 fingerprint is usually faster and because it is
only half the size of the SHA-512 fingerprint, [`x509.fingerprint256`][] may be
a better choice. While SHA-512 presumably provides a higher level of security in
general, the security of SHA-256 matches that of most algorithms that are
commonly used to sign certificates.
