### Error handling

There are several types of error conditions that may arise when using the
`node:http2` module:

Validation errors occur when an incorrect argument, option, or setting value is
passed in. These will always be reported by a synchronous `throw`.

State errors occur when an action is attempted at an incorrect time (for
instance, attempting to send data on a stream after it has closed). These will
be reported using either a synchronous `throw` or via an `'error'` event on
the `Http2Stream`, `Http2Session` or HTTP/2 Server objects, depending on where
and when the error occurs.

Internal errors occur when an HTTP/2 session fails unexpectedly. These will be
reported via an `'error'` event on the `Http2Session` or HTTP/2 Server objects.

Protocol errors occur when various HTTP/2 protocol constraints are violated.
These will be reported using either a synchronous `throw` or via an `'error'`
event on the `Http2Stream`, `Http2Session` or HTTP/2 Server objects, depending
on where and when the error occurs.
