## `net.isIPv4(input)`

<!-- YAML
added: v0.3.0
-->

* `input` {string}
* Returns: {boolean}

Returns `true` if `input` is an IPv4 address in [dot-decimal notation][] with no
leading zeroes. Otherwise, returns `false`.

```js
net.isIPv4('127.0.0.1'); // returns true
net.isIPv4('127.000.000.001'); // returns false
net.isIPv4('127.0.0.1/24'); // returns false
net.isIPv4('fhqwhgads'); // returns false
```
