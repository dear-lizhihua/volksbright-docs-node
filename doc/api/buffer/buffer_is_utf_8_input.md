### `buffer.isUtf8(input)`

<!-- YAML
added:
  - v19.4.0
  - v18.14.0
-->

* input {Buffer | ArrayBuffer | TypedArray} The input to validate.
* Returns: {boolean}

This function returns `true` if `input` contains only valid UTF-8-encoded data,
including the case in which `input` is empty.

Throws if the `input` is a detached array buffer.
