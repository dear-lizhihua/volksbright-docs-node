### `hash.digest([encoding])`

<!-- YAML
added: v0.1.92
-->

* `encoding` {string} The [encoding][] of the return value.
* Returns: {Buffer | string}

Calculates the digest of all of the data passed to be hashed (using the
[`hash.update()`][] method).
If `encoding` is provided a string will be returned; otherwise
a [`Buffer`][] is returned.

The `Hash` object can not be used again after `hash.digest()` method has been
called. Multiple calls will cause an error to be thrown.
