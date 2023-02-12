## `dns.getServers()`

<!-- YAML
added: v0.11.3
-->

* Returns: {string\[]}

Returns an array of IP address strings, formatted according to [RFC 5952][],
that are currently configured for DNS resolution. A string will include a port
section if a custom port is used.

<!-- eslint-disable semi-->

```js
[
  '4.4.4.4',
  '2001:4860:4860::8888',
  '4.4.4.4:1053',
  '[2001:4860:4860::8888]:1053',
]
```
