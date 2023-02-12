### Event: `'socket'`

<!-- YAML
added: v0.5.3
-->

* `socket` {stream.Duplex}

This event is guaranteed to be passed an instance of the {net.Socket} class,
a subclass of {stream.Duplex}, unless the user specifies a socket
type other than {net.Socket}.
