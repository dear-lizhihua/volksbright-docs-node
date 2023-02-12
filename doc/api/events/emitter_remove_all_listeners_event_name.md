### `emitter.removeAllListeners([eventName])`

<!-- YAML
added: v0.1.26
-->

* `eventName` {string|symbol}
* Returns: {EventEmitter}

Removes all listeners, or those of the specified `eventName`.

It is bad practice to remove listeners added elsewhere in the code,
particularly when the `EventEmitter` instance was created by some other
component or module (e.g. sockets or file streams).

Returns a reference to the `EventEmitter`, so that calls can be chained.
