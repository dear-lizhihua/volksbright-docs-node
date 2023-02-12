### `x509.fingerprint`

<!-- YAML
added: v15.6.0
-->

* Type: {string}

The SHA-1 fingerprint of this certificate.

Because SHA-1 is cryptographically broken and because the security of SHA-1 is
significantly worse than that of algorithms that are commonly used to sign
certificates, consider using [`x509.fingerprint256`][] instead.
