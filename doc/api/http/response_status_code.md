### `response.statusCode`

<!-- YAML
added: v0.4.0
-->

* {number} **Default:** `200`

When using implicit headers (not calling [`response.writeHead()`][] explicitly),
this property controls the status code that will be sent to the client when
the headers get flushed.

```js
response.statusCode = 404;
```

After response header was sent to the client, this property indicates the
status code which was sent out.
