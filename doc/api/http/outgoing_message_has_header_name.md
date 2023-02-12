### `outgoingMessage.hasHeader(name)`

<!-- YAML
added: v7.7.0
-->

* `name` {string}
* Returns {boolean}

Returns `true` if the header identified by `name` is currently set in the
outgoing headers. The header name is case-insensitive.

```js
const hasContentType = outgoingMessage.hasHeader('content-type');
```
