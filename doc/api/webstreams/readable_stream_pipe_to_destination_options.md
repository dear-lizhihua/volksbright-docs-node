#### `readableStream.pipeTo(destination[, options])`

<!-- YAML
added: v16.5.0
-->

* `destination` {WritableStream} A {WritableStream} to which this
  `ReadableStream`'s data will be written.
* `options` {Object}
  * `preventAbort` {boolean} When `true`, errors in this `ReadableStream`
    will not cause `destination` to be aborted.
  * `preventCancel` {boolean} When `true`, errors in the `destination`
    will not cause this `ReadableStream` to be canceled.
  * `preventClose` {boolean} When `true`, closing this `ReadableStream`
    does not cause `destination` to be closed.
  * `signal` {AbortSignal} Allows the transfer of data to be canceled
    using an {AbortController}.
* Returns: A promise fulfilled with `undefined`

Causes the `readableStream.locked` to be `true` while the pipe operation
is active.
