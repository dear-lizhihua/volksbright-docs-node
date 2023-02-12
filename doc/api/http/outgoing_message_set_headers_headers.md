### `outgoingMessage.setHeaders(headers)`

<!-- YAML
added: v19.6.0
-->

* `headers` {Headers|Map}
* Returns: {http.ServerResponse}

Returns the response object.

Sets multiple header values for implicit headers.
`headers` must be an instance of [`Headers`][] or `Map`,
if a header already exists in the to-be-sent headers,
its value will be replaced.

```js
const headers = new Headers({ foo: 'bar' });
response.setHeaders(headers);
```

or

```js
const headers = new Map([['foo', 'bar']]);
res.setHeaders(headers);
```

When headers have been set with [`outgoingMessage.setHeaders()`][],
they will be merged with any headers passed to [`response.writeHead()`][],
with the headers passed to [`response.writeHead()`][] given precedence.

```js
// Returns content-type = text/plain
const server = http.createServer((req, res) => {
  const headers = new Headers({ 'Content-Type': 'text/html' });
  res.setHeaders(headers);
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('ok');
});
```
