### `v8.serialize(value)`

<!-- YAML
added: v8.0.0
-->

* `value` {any}
* Returns: {Buffer}

Uses a [`DefaultSerializer`][] to serialize `value` into a buffer.

[`ERR_BUFFER_TOO_LARGE`][] will be thrown when trying to
serialize a huge object which requires buffer
larger than [`buffer.constants.MAX_LENGTH`][].
