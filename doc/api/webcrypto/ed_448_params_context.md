#### `ed448Params.context`

<!-- YAML
added:
  - v18.4.0
  - v16.17.0
-->

* Type: {ArrayBuffer|TypedArray|DataView|Buffer|undefined}

The `context` member represents the optional context data to associate with
the message.
The Node.js Web Crypto API implementation only supports zero-length context
which is equivalent to not providing context at all.
