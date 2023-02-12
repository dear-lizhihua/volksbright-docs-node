## `net.createServer([options][, connectionListener])`

<!-- YAML
added: v0.5.0
changes:
  - version:
    - v17.7.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41310
    description: The `noDelay`, `keepAlive`, and `keepAliveInitialDelay`
                 options are supported now.
-->

* `options` {Object}
  * `allowHalfOpen` {boolean} If set to `false`, then the socket will
    automatically end the writable side when the readable side ends.
    **Default:** `false`.
  * `pauseOnConnect` {boolean} Indicates whether the socket should be
    paused on incoming connections. **Default:** `false`.
  * `noDelay` {boolean} If set to `true`, it disables the use of Nagle's algorithm immediately
    after a new incoming connection is received. **Default:** `false`.
  * `keepAlive` {boolean} If set to `true`, it enables keep-alive functionality on the socket
    immediately after a new incoming connection is received, similarly on what is done in
    [`socket.setKeepAlive([enable][, initialDelay])`][`socket.setKeepAlive(enable, initialDelay)`].
    **Default:** `false`.
  * `keepAliveInitialDelay` {number} If set to a positive number, it sets the initial delay before
    the first keepalive probe is sent on an idle socket.**Default:** `0`.

* `connectionListener` {Function} Automatically set as a listener for the
  [`'connection'`][] event.

* Returns: {net.Server}

Creates a new TCP or [IPC][] server.

If `allowHalfOpen` is set to `true`, when the other end of the socket
signals the end of transmission, the server will only send back the end of
transmission when [`socket.end()`][] is explicitly called. For example, in the
context of TCP, when a FIN packed is received, a FIN packed is sent
back only when [`socket.end()`][] is explicitly called. Until then the
connection is half-closed (non-readable but still writable). See [`'end'`][]
event and [RFC 1122][half-closed] (section 4.2.2.13) for more information.

If `pauseOnConnect` is set to `true`, then the socket associated with each
incoming connection will be paused, and no data will be read from its handle.
This allows connections to be passed between processes without any data being
read by the original process. To begin reading data from a paused socket, call
[`socket.resume()`][].

The server can be a TCP server or an [IPC][] server, depending on what it
[`listen()`][`server.listen()`] to.

Here is an example of a TCP echo server which listens for connections
on port 8124:

```js
const net = require('node:net');
const server = net.createServer((c) => {
  // 'connection' listener.
  console.log('client connected');
  c.on('end', () => {
    console.log('client disconnected');
  });
  c.write('hello\r\n');
  c.pipe(c);
});
server.on('error', (err) => {
  throw err;
});
server.listen(8124, () => {
  console.log('server bound');
});
```

Test this by using `telnet`:

```console
$ telnet localhost 8124
```

To listen on the socket `/tmp/echo.sock`:

```js
server.listen('/tmp/echo.sock', () => {
  console.log('server bound');
});
```

Use `nc` to connect to a Unix domain socket server:

```console
$ nc -U /tmp/echo.sock
```
