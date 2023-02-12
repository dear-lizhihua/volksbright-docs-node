### `message.headersDistinct`

<!-- YAML
added:
  - v18.3.0
  - v16.17.0
-->

* {Object}

Similar to [`message.headers`][], but there is no join logic and the values are
always arrays of strings, even for headers received just once.

```js
// Prints something like:
//
// { 'user-agent': ['curl/7.22.0'],
//   host: ['127.0.0.1:8000'],
//   accept: ['*/*'] }
console.log(request.headersDistinct);
```
