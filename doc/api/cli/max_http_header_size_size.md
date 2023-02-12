### `--max-http-header-size=size`

<!-- YAML
added:
 - v11.6.0
 - v10.15.0
changes:
  - version: v13.13.0
    pr-url: https://github.com/nodejs/node/pull/32520
    description: Change maximum default size of HTTP headers from 8 KiB to 16 KiB.
-->

Specify the maximum size, in bytes, of HTTP headers. Defaults to 16 KiB.
