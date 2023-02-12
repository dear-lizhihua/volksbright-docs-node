## `util.stripVTControlCharacters(str)`

<!-- YAML
added: v16.11.0
-->

* `str` {string}
* Returns: {string}

Returns `str` with any ANSI escape codes removed.

```js
console.log(util.stripVTControlCharacters('\u001B[4mvalue\u001B[0m'));
// Prints "value"
```
