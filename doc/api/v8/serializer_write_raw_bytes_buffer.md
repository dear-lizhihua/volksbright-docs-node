#### `serializer.writeRawBytes(buffer)`

* `buffer` {Buffer|TypedArray|DataView}

Write raw bytes into the serializer's internal buffer. The deserializer
will require a way to compute the length of the buffer.
For use inside of a custom [`serializer._writeHostObject()`][].
