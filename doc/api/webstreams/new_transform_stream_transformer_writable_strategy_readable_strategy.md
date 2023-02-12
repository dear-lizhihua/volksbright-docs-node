#### `new TransformStream([transformer[, writableStrategy[, readableStrategy]]])`

<!-- YAML
added: v16.5.0
-->

* `transformer` {Object}
  * `start` {Function} A user-defined function that is invoked immediately when
    the `TransformStream` is created.
    * `controller` {TransformStreamDefaultController}
    * Returns: `undefined` or a promise fulfilled with `undefined`
  * `transform` {Function} A user-defined function that receives, and
    potentially modifies, a chunk of data written to `transformStream.writable`,
    before forwarding that on to `transformStream.readable`.
    * `chunk` {any}
    * `controller` {TransformStreamDefaultController}
    * Returns: A promise fulfilled with `undefined`.
  * `flush` {Function} A user-defined function that is called immediately before
    the writable side of the `TransformStream` is closed, signaling the end of
    the transformation process.
    * `controller` {TransformStreamDefaultController}
    * Returns: A promise fulfilled with `undefined`.
  * `readableType` {any} the `readableType` option is reserved for future use
    and _must_ be `undefined`.
  * `writableType` {any} the `writableType` option is reserved for future use
    and _must_ be `undefined`.
* `writableStrategy` {Object}
  * `highWaterMark` {number} The maximum internal queue size before backpressure
    is applied.
  * `size` {Function} A user-defined function used to identify the size of each
    chunk of data.
    * `chunk` {any}
    * Returns: {number}
* `readableStrategy` {Object}
  * `highWaterMark` {number} The maximum internal queue size before backpressure
    is applied.
  * `size` {Function} A user-defined function used to identify the size of each
    chunk of data.
    * `chunk` {any}
    * Returns: {number}
