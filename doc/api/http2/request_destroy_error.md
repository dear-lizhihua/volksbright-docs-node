#### `request.destroy([error])`

<!-- YAML
added: v8.4.0
-->

* `error` {Error}

Calls `destroy()` on the [`Http2Stream`][] that received
the [`Http2ServerRequest`][]. If `error` is provided, an `'error'` event
is emitted and `error` is passed as an argument to any listeners on the event.

It does nothing if the stream was already destroyed.
