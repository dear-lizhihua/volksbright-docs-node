#### Event: `'push'`

<!-- YAML
added: v8.4.0
-->

* `headers` {HTTP/2 Headers Object}
* `flags` {number}

The `'push'` event is emitted when response headers for a Server Push stream
are received. The listener callback is passed the [HTTP/2 Headers Object][] and
flags associated with the headers.

```js
stream.on('push', (headers, flags) => {
  console.log(headers);
});
```
