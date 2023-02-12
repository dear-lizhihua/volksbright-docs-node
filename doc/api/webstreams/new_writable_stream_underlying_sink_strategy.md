#### `new WritableStream([underlyingSink[, strategy]])`

<!-- YAML
added: v16.5.0
-->

* `underlyingSink` {Object}
  * `start` {Function} A user-defined function that is invoked immediately when
    the `WritableStream` is created.
    * `controller` {WritableStreamDefaultController}
    * Returns: `undefined` or a promise fulfilled with `undefined`.
  * `write` {Function} A user-defined function that is invoked when a chunk of
    data has been written to the `WritableStream`.
    * `chunk` {any}
    * `controller` {WritableStreamDefaultController}
    * Returns: A promise fulfilled with `undefined`.
  * `close` {Function} A user-defined function that is called when the
    `WritableStream` is closed.
    * Returns: A promise fulfilled with `undefined`.
  * `abort` {Function} A user-defined function that is called to abruptly close
    the `WritableStream`.
    * `reason` {any}
    * Returns: A promise fulfilled with `undefined`.
  * `type` {any} The `type` option is reserved for future use and _must_ be
    undefined.
* `strategy` {Object}
  * `highWaterMark` {number} The maximum internal queue size before backpressure
    is applied.
  * `size` {Function} A user-defined function used to identify the size of each
    chunk of data.
    * `chunk` {any}
    * Returns: {number}
