## `net.isIP(input)`

<!-- YAML
added: v0.3.0
-->

* `input` {string}
* Returns: {integer}

Returns `6` if `input` is an IPv6 address. Returns `4` if `input` is an IPv4
address in [dot-decimal notation][] with no leading zeroes. Otherwise, returns
`0`.

```js
net.isIP('::1'); // returns 6
net.isIP('127.0.0.1'); // returns 4
net.isIP('127.000.000.001'); // returns 0
net.isIP('127.0.0.1/24'); // returns 0
net.isIP('fhqwhgads'); // returns 0
```
