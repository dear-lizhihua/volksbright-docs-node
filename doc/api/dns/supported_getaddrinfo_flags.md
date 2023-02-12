### Supported getaddrinfo flags

<!-- YAML
changes:
  - version:
     - v13.13.0
     - v12.17.0
    pr-url: https://github.com/nodejs/node/pull/32183
    description: Added support for the `dns.ALL` flag.
-->

The following flags can be passed as hints to [`dns.lookup()`][].

* `dns.ADDRCONFIG`: Limits returned address types to the types of non-loopback
  addresses configured on the system. For example, IPv4 addresses are only
  returned if the current system has at least one IPv4 address configured.
* `dns.V4MAPPED`: If the IPv6 family was specified, but no IPv6 addresses were
  found, then return IPv4 mapped IPv6 addresses. It is not supported
  on some operating systems (e.g. FreeBSD 10.1).
* `dns.ALL`: If `dns.V4MAPPED` is specified, return resolved IPv6 addresses as
  well as IPv4 mapped IPv6 addresses.
