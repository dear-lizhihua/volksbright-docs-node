### `keyObject.asymmetricKeyDetails`

<!-- YAML
added: v15.7.0
changes:
  - version: v16.9.0
    pr-url: https://github.com/nodejs/node/pull/39851
    description: Expose `RSASSA-PSS-params` sequence parameters
                 for RSA-PSS keys.
-->

* {Object}
  * `modulusLength`: {number} Key size in bits (RSA, DSA).
  * `publicExponent`: {bigint} Public exponent (RSA).
  * `hashAlgorithm`: {string} Name of the message digest (RSA-PSS).
  * `mgf1HashAlgorithm`: {string} Name of the message digest used by
    MGF1 (RSA-PSS).
  * `saltLength`: {number} Minimal salt length in bytes (RSA-PSS).
  * `divisorLength`: {number} Size of `q` in bits (DSA).
  * `namedCurve`: {string} Name of the curve (EC).

This property exists only on asymmetric keys. Depending on the type of the key,
this object contains information about the key. None of the information obtained
through this property can be used to uniquely identify a key or to compromise
the security of the key.

For RSA-PSS keys, if the key material contains a `RSASSA-PSS-params` sequence,
the `hashAlgorithm`, `mgf1HashAlgorithm`, and `saltLength` properties will be
set.

Other key details might be exposed via this API using additional attributes.
