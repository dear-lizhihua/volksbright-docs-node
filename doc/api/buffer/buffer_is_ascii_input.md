### `buffer.isAscii(input)`

<!-- YAML
added: v19.6.0
-->

* input {Buffer | ArrayBuffer | TypedArray} The input to validate.
* Returns: {boolean}

This function returns `true` if `input` contains only valid ASCII-encoded data,
including the case in which `input` is empty.

Throws if the `input` is a detached array buffer.
