### `ERR_CLOSED_MESSAGE_PORT`

<!--
added:
  - v16.2.0
  - v14.17.1
changes:
  - version: 11.12.0
    pr-url: https://github.com/nodejs/node/pull/26487
    description: The error message was removed.
  - version:
      - v16.2.0
      - v14.17.1
    pr-url: https://github.com/nodejs/node/pull/38510
    description: The error message was reintroduced.
-->

There was an attempt to use a `MessagePort` instance in a closed
state, usually after `.close()` has been called.

<a id="ERR_CONSOLE_WRITABLE_STREAM"></a>
