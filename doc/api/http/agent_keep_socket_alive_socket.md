### `agent.keepSocketAlive(socket)`

<!-- YAML
added: v8.1.0
-->

* `socket` {stream.Duplex}

Called when `socket` is detached from a request and could be persisted by the
`Agent`. Default behavior is to:

```js
socket.setKeepAlive(true, this.keepAliveMsecs);
socket.unref();
return true;
```

This method can be overridden by a particular `Agent` subclass. If this
method returns a falsy value, the socket will be destroyed instead of persisting
it for use with the next request.

The `socket` argument can be an instance of {net.Socket}, a subclass of
{stream.Duplex}.
