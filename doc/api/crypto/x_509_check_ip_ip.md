### `x509.checkIP(ip)`

<!-- YAML
added: v15.6.0
changes:
  - version:
      - v17.5.0
      - v16.14.1
    pr-url: https://github.com/nodejs/node/pull/41571
    description: The `options` argument has been removed since it had no effect.
-->

* `ip` {string}
* Returns: {string|undefined} Returns `ip` if the certificate matches,
  `undefined` if it does not.

Checks whether the certificate matches the given IP address (IPv4 or IPv6).

Only [RFC 5280][] `iPAddress` subject alternative names are considered, and they
must match the given `ip` address exactly. Other subject alternative names as
well as the subject field of the certificate are ignored.
