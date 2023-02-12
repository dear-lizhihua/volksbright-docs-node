## Class: `Verify`

<!-- YAML
added: v0.1.92
-->

* Extends: {stream.Writable}

The `Verify` class is a utility for verifying signatures. It can be used in one
of two ways:

* As a writable [stream][] where written data is used to validate against the
  supplied signature, or
* Using the [`verify.update()`][] and [`verify.verify()`][] methods to verify
  the signature.

The [`crypto.createVerify()`][] method is used to create `Verify` instances.
`Verify` objects are not to be created directly using the `new` keyword.

See [`Sign`][] for examples.
