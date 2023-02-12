#### `readableStream.tee()`

<!-- YAML
added: v16.5.0
changes:
  - version:
    - v18.10.0
    - v16.18.0
    pr-url: https://github.com/nodejs/node/pull/44505
    description: Support teeing a readable byte stream.
-->

* Returns: {ReadableStream\[]}

Returns a pair of new {ReadableStream} instances to which this
`ReadableStream`'s data will be forwarded. Each will receive the
same data.

Causes the `readableStream.locked` to be `true`.
