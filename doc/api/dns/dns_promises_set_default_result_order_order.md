### `dnsPromises.setDefaultResultOrder(order)`

<!-- YAML
added:
  - v16.4.0
  - v14.18.0
changes:
  - version: v17.0.0
    pr-url: https://github.com/nodejs/node/pull/39987
    description: Changed default value to `verbatim`.
-->

* `order` {string} must be `'ipv4first'` or `'verbatim'`.

Set the default value of `verbatim` in [`dns.lookup()`][] and
[`dnsPromises.lookup()`][]. The value could be:

* `ipv4first`: sets default `verbatim` `false`.
* `verbatim`: sets default `verbatim` `true`.

The default is `verbatim` and [`dnsPromises.setDefaultResultOrder()`][] have
higher priority than [`--dns-result-order`][]. When using [worker threads][],
[`dnsPromises.setDefaultResultOrder()`][] from the main thread won't affect the
default dns orders in workers.
