#### Event: `'headers'`

<!-- YAML
added: v8.4.0
-->

* `headers` {HTTP/2 Headers Object}
* `flags` {number}

The `'headers'` event is emitted when an additional block of headers is received
for a stream, such as when a block of `1xx` informational headers is received.
The listener callback is passed the [HTTP/2 Headers Object][] and flags
associated with the headers.

```js
stream.on('headers', (headers, flags) => {
  console.log(headers);
});
```
