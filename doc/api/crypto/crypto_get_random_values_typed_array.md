### `crypto.getRandomValues(typedArray)`

<!-- YAML
added: v17.4.0
-->

* `typedArray` {Buffer|TypedArray|DataView|ArrayBuffer}
* Returns: {Buffer|TypedArray|DataView|ArrayBuffer} Returns `typedArray`.

A convenient alias for [`crypto.webcrypto.getRandomValues()`][]. This
implementation is not compliant with the Web Crypto spec, to write
web-compatible code use [`crypto.webcrypto.getRandomValues()`][] instead.
