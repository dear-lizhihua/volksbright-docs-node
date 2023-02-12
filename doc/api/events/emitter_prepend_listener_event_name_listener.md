### `emitter.prependListener(eventName, listener)`

<!-- YAML
added: v6.0.0
-->

* `eventName` {string|symbol} The name of the event.
* `listener` {Function} The callback function
* Returns: {EventEmitter}

Adds the `listener` function to the _beginning_ of the listeners array for the
event named `eventName`. No checks are made to see if the `listener` has
already been added. Multiple calls passing the same combination of `eventName`
and `listener` will result in the `listener` being added, and called, multiple
times.

```js
server.prependListener('connection', (stream) => {
  console.log('someone connected!');
});
```

Returns a reference to the `EventEmitter`, so that calls can be chained.
