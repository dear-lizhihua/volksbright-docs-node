### `new Agent([options])`

<!-- YAML
changes:
  - version: v12.5.0
    pr-url: https://github.com/nodejs/node/pull/28209
    description: do not automatically set servername if the target host was
                 specified using an IP address.
-->

* `options` {Object} Set of configurable options to set on the agent.
  Can have the same fields as for [`http.Agent(options)`][], and
  * `maxCachedSessions` {number} maximum number of TLS cached sessions.
    Use `0` to disable TLS session caching. **Default:** `100`.
  * `servername` {string} the value of
    [Server Name Indication extension][sni wiki] to be sent to the server. Use
    empty string `''` to disable sending the extension.
    **Default:** host name of the target server, unless the target server
    is specified using an IP address, in which case the default is `''` (no
    extension).

    See [`Session Resumption`][] for information about TLS session reuse.
