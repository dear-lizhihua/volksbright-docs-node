### Event: `'finish'`

<!-- YAML
added: v0.3.6
-->

Emitted when the request has been sent. More specifically, this event is emitted
when the last segment of the response headers and body have been handed off to
the operating system for transmission over the network. It does not imply that
the server has received anything yet.
