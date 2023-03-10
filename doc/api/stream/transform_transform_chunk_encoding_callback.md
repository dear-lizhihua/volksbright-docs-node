#### `transform._transform(chunk, encoding, callback)`

* `chunk` {Buffer|string|any} The `Buffer` to be transformed, converted from
  the `string` passed to [`stream.write()`][stream-write]. If the stream's
  `decodeStrings` option is `false` or the stream is operating in object mode,
  the chunk will not be converted & will be whatever was passed to
  [`stream.write()`][stream-write].
* `encoding` {string} If the chunk is a string, then this is the
  encoding type. If chunk is a buffer, then this is the special
  value `'buffer'`. Ignore it in that case.
* `callback` {Function} A callback function (optionally with an error
  argument and data) to be called after the supplied `chunk` has been
  processed.

This function MUST NOT be called by application code directly. It should be
implemented by child classes, and called by the internal `Readable` class
methods only.

All `Transform` stream implementations must provide a `_transform()`
method to accept input and produce output. The `transform._transform()`
implementation handles the bytes being written, computes an output, then passes
that output off to the readable portion using the `transform.push()` method.

The `transform.push()` method may be called zero or more times to generate
output from a single input chunk, depending on how much is to be output
as a result of the chunk.

It is possible that no output is generated from any given chunk of input data.

The `callback` function must be called only when the current chunk is completely
consumed. The first argument passed to the `callback` must be an `Error` object
if an error occurred while processing the input or `null` otherwise. If a second
argument is passed to the `callback`, it will be forwarded on to the
`transform.push()` method. In other words, the following are equivalent:

```js
transform.prototype._transform = function(data, encoding, callback) {
  this.push(data);
  callback();
};

transform.prototype._transform = function(data, encoding, callback) {
  callback(null, data);
};
```

The `transform._transform()` method is prefixed with an underscore because it
is internal to the class that defines it, and should never be called directly by
user programs.

`transform._transform()` is never called in parallel; streams implement a
queue mechanism, and to receive the next chunk, `callback` must be
called, either synchronously or asynchronously.
