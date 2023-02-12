#### `socket.connect(options[, connectListener])`

<!-- YAML
added: v0.1.90
changes:
  - version: v19.4.0
    pr-url: https://github.com/nodejs/node/pull/45777
    description: The default value for autoSelectFamily option can be changed
                 at runtime using `setDefaultAutoSelectFamily` or via the
                 command line option `--enable-network-family-autoselection`.
  - version:
      - v19.3.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/44731
    description: Added the `autoSelectFamily` option.
  - version:
    - v17.7.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41310
    description: The `noDelay`, `keepAlive`, and `keepAliveInitialDelay`
                 options are supported now.
  - version: v12.10.0
    pr-url: https://github.com/nodejs/node/pull/25436
    description: Added `onread` option.
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/6021
    description: The `hints` option defaults to `0` in all cases now.
                 Previously, in the absence of the `family` option it would
                 default to `dns.ADDRCONFIG | dns.V4MAPPED`.
  - version: v5.11.0
    pr-url: https://github.com/nodejs/node/pull/6000
    description: The `hints` option is supported now.
-->

* `options` {Object}
* `connectListener` {Function} Common parameter of [`socket.connect()`][]
  methods. Will be added as a listener for the [`'connect'`][] event once.
* Returns: {net.Socket} The socket itself.

Initiate a connection on a given socket. Normally this method is not needed,
the socket should be created and opened with [`net.createConnection()`][]. Use
this only when implementing a custom Socket.

For TCP connections, available `options` are:

* `port` {number} Required. Port the socket should connect to.
* `host` {string} Host the socket should connect to. **Default:** `'localhost'`.
* `localAddress` {string} Local address the socket should connect from.
* `localPort` {number} Local port the socket should connect from.
* `family` {number}: Version of IP stack. Must be `4`, `6`, or `0`. The value
  `0` indicates that both IPv4 and IPv6 addresses are allowed. **Default:** `0`.
* `hints` {number} Optional [`dns.lookup()` hints][].
* `lookup` {Function} Custom lookup function. **Default:** [`dns.lookup()`][].
* `noDelay` {boolean} If set to `true`, it disables the use of Nagle's algorithm immediately
  after the socket is established. **Default:** `false`.
* `keepAlive` {boolean} If set to `true`, it enables keep-alive functionality on the socket
  immediately after the connection is established, similarly on what is done in
  [`socket.setKeepAlive([enable][, initialDelay])`][`socket.setKeepAlive(enable, initialDelay)`].
  **Default:** `false`.
* `keepAliveInitialDelay` {number} If set to a positive number, it sets the initial delay before
  the first keepalive probe is sent on an idle socket.**Default:** `0`.
* `autoSelectFamily` {boolean}: If set to `true`, it enables a family autodetection algorithm
  that loosely implements section 5 of [RFC 8305][].
  The `all` option passed to lookup is set to `true` and the sockets attempts to connect to all
  obtained IPv6 and IPv4 addresses, in sequence, until a connection is established.
  The first returned AAAA address is tried first, then the first returned A address,
  then the second returned AAAA address and so on.
  Each connection attempt is given the amount of time specified by the `autoSelectFamilyAttemptTimeout`
  option before timing out and trying the next address.
  Ignored if the `family` option is not `0` or if `localAddress` is set.
  Connection errors are not emitted if at least one connection succeeds.
  **Default:** initially `false`, but it can be changed at runtime using [`net.setDefaultAutoSelectFamily(value)`][]
  or via the command line option `--enable-network-family-autoselection`.
* `autoSelectFamilyAttemptTimeout` {number}: The amount of time in milliseconds to wait
  for a connection attempt to finish before trying the next address when using the `autoSelectFamily` option.
  If set to a positive integer less than `10`, then the value `10` will be used instead.
  **Default:** `250`.

For [IPC][] connections, available `options` are:

* `path` {string} Required. Path the client should connect to.
  See [Identifying paths for IPC connections][]. If provided, the TCP-specific
  options above are ignored.

For both types, available `options` include:

* `onread` {Object} If specified, incoming data is stored in a single `buffer`
  and passed to the supplied `callback` when data arrives on the socket.
  This will cause the streaming functionality to not provide any data.
  The socket will emit events like `'error'`, `'end'`, and `'close'`
  as usual. Methods like `pause()` and `resume()` will also behave as
  expected.
  * `buffer` {Buffer|Uint8Array|Function} Either a reusable chunk of memory to
    use for storing incoming data or a function that returns such.
  * `callback` {Function} This function is called for every chunk of incoming
    data. Two arguments are passed to it: the number of bytes written to
    `buffer` and a reference to `buffer`. Return `false` from this function to
    implicitly `pause()` the socket. This function will be executed in the
    global context.

Following is an example of a client using the `onread` option:

```js
const net = require('node:net');
net.connect({
  port: 80,
  onread: {
    // Reuses a 4KiB Buffer for every read from the socket.
    buffer: Buffer.alloc(4 * 1024),
    callback: function(nread, buf) {
      // Received data is available in `buf` from 0 to `nread`.
      console.log(buf.toString('utf8', 0, nread));
    },
  },
});
```
