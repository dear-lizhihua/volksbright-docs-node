#### HTTP

`http.client.request.start`

* `request` {http.ClientRequest}

Emitted when client starts a request.

`http.client.response.finish`

* `request` {http.ClientRequest}
* `response` {http.IncomingMessage}

Emitted when client receives a response.

`http.server.request.start`

* `request` {http.IncomingMessage}
* `response` {http.ServerResponse}
* `socket` {net.Socket}
* `server` {http.Server}

Emitted when server receives a request.

`http.server.response.finish`

* `request` {http.IncomingMessage}
* `response` {http.ServerResponse}
* `socket` {net.Socket}
* `server` {http.Server}

Emitted when server sends a response.
