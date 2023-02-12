### `agent.createConnection(options[, callback])`

<!-- YAML
added: v0.11.4
-->

* `options` {Object} Options containing connection details. Check
  [`net.createConnection()`][] for the format of the options
* `callback` {Function} Callback function that receives the created socket
* Returns: {stream.Duplex}

Produces a socket/stream to be used for HTTP requests.

By default, this function is the same as [`net.createConnection()`][]. However,
custom agents may override this method in case greater flexibility is desired.

A socket/stream can be supplied in one of two ways: by returning the
socket/stream from this function, or by passing the socket/stream to `callback`.

This method is guaranteed to return an instance of the {net.Socket} class,
a subclass of {stream.Duplex}, unless the user specifies a socket
type other than {net.Socket}.

`callback` has a signature of `(err, stream)`.
