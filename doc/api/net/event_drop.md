### Event: `'drop'`

<!-- YAML
added:
  - v18.6.0
  - v16.17.0
-->

When the number of connections reaches the threshold of `server.maxConnections`,
the server will drop new connections and emit `'drop'` event instead. If it is a
TCP server, the argument is as follows, otherwise the argument is `undefined`.

* `data` {Object} The argument passed to event listener.
  * `localAddress` {string}  Local address.
  * `localPort` {number} Local port.
  * `localFamily` {string} Local family.
  * `remoteAddress` {string} Remote address.
  * `remotePort` {number} Remote port.
  * `remoteFamily` {string} Remote IP family. `'IPv4'` or `'IPv6'`.
