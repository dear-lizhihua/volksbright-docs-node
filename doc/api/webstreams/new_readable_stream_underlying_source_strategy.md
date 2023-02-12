#### `new ReadableStream([underlyingSource [, strategy]])`

<!-- YAML
added: v16.5.0
-->

<!--lint disable maximum-line-length remark-lint-->

* `underlyingSource` {Object}
  * `start` {Function} A user-defined function that is invoked immediately when
    the `ReadableStream` is created.
    * `controller` {ReadableStreamDefaultController|ReadableByteStreamController}
    * Returns: `undefined` or a promise fulfilled with `undefined`.
  * `pull` {Function} A user-defined function that is called repeatedly when the
    `ReadableStream` internal queue is not full. The operation may be sync or
    async. If async, the function will not be called again until the previously
    returned promise is fulfilled.
    * `controller` {ReadableStreamDefaultController|ReadableByteStreamController}
    * Returns: A promise fulfilled with `undefined`.
  * `cancel` {Function} A user-defined function that is called when the
    `ReadableStream` is canceled.
    * `reason` {any}
    * Returns: A promise fulfilled with `undefined`.
  * `type` {string} Must be `'bytes'` or `undefined`.
  * `autoAllocateChunkSize` {number} Used only when `type` is equal to
    `'bytes'`.
* `strategy` {Object}
  * `highWaterMark` {number} The maximum internal queue size before backpressure
    is applied.
  * `size` {Function} A user-defined function used to identify the size of each
    chunk of data.
    * `chunk` {any}
    * Returns: {number}

<!--lint enable maximum-line-length remark-lint-->
