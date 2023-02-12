## `dns.resolve6(hostname[, options], callback)`

<!-- YAML
added: v0.1.16
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41678
    description: Passing an invalid callback to the `callback` argument
                 now throws `ERR_INVALID_ARG_TYPE` instead of
                 `ERR_INVALID_CALLBACK`.
  - version: v7.2.0
    pr-url: https://github.com/nodejs/node/pull/9296
    description: This method now supports passing `options`,
                 specifically `options.ttl`.
-->

* `hostname` {string} Host name to resolve.
* `options` {Object}
  * `ttl` {boolean} Retrieve the Time-To-Live value (TTL) of each record.
    When `true`, the callback receives an array of
    `{ address: '0:1:2:3:4:5:6:7', ttl: 60 }` objects rather than an array of
    strings, with the TTL expressed in seconds.
* `callback` {Function}
  * `err` {Error}
  * `addresses` {string\[] | Object\[]}

Uses the DNS protocol to resolve IPv6 addresses (`AAAA` records) for the
`hostname`. The `addresses` argument passed to the `callback` function
will contain an array of IPv6 addresses.
