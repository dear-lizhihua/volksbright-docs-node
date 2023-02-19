### `error.code`

* {string}

The `error.code` property is a string label that identifies the kind of error.
`error.code` is the most stable way to identify an error. It will only change
between major versions of Node.js. In contrast, `error.message` strings may
change between any versions of Node.js. See [Node.js error codes][] for details
about specific codes.
