#### Event: `'response'`

<!-- YAML
added: v8.4.0
-->

* `headers` {HTTP/2 Headers Object}
* `flags` {number}

The `'response'` event is emitted when a response `HEADERS` frame has been
received for this stream from the connected HTTP/2 server. The listener is
invoked with two arguments: an `Object` containing the received
[HTTP/2 Headers Object][], and flags associated with the headers.

```js
const http2 = require('node:http2');
const client = http2.connect('https://localhost');
const req = client.request({ ':path': '/' });
req.on('response', (headers, flags) => {
  console.log(headers[':status']);
});
```
