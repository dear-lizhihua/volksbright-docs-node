#### `readableStream.locked`

<!-- YAML
added: v16.5.0
-->

* Type: {boolean} Set to `true` if there is an active reader for this
  {ReadableStream}.

The `readableStream.locked` property is `false` by default, and is
switched to `true` while there is an active reader consuming the
stream's data.
