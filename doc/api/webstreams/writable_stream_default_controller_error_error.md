#### `writableStreamDefaultController.error([error])`

<!-- YAML
added: v16.5.0
-->

* `error` {any}

Called by user-code to signal that an error has occurred while processing
the `WritableStream` data. When called, the {WritableStream} will be aborted,
with currently pending writes canceled.
