### `x509.serialNumber`

<!-- YAML
added: v15.6.0
-->

* Type: {string}

The serial number of this certificate.

Serial numbers are assigned by certificate authorities and do not uniquely
identify certificates. Consider using [`x509.fingerprint256`][] as a unique
identifier instead.
