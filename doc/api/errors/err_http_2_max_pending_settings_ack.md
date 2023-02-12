### `ERR_HTTP2_MAX_PENDING_SETTINGS_ACK`

Whenever an HTTP/2 `SETTINGS` frame is sent to a connected peer, the peer is
required to send an acknowledgment that it has received and applied the new
`SETTINGS`. By default, a maximum number of unacknowledged `SETTINGS` frames may
be sent at any given time. This error code is used when that limit has been
reached.

<a id="ERR_HTTP2_NESTED_PUSH"></a>
