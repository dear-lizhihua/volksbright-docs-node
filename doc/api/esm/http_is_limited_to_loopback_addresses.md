### HTTP is limited to loopback addresses

`http:` is vulnerable to man-in-the-middle attacks and is not allowed to be
used for addresses outside of the IPv4 address `127.0.0.0/8` (`127.0.0.1` to
`127.255.255.255`) and the IPv6 address `::1`. Support for `http:` is intended
to be used for local development.
