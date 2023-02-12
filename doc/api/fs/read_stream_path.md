#### `readStream.path`

<!-- YAML
added: v0.1.93
-->

* {string|Buffer}

The path to the file the stream is reading from as specified in the first
argument to `fs.createReadStream()`. If `path` is passed as a string, then
`readStream.path` will be a string. If `path` is passed as a {Buffer}, then
`readStream.path` will be a {Buffer}. If `fd` is specified, then
`readStream.path` will be `undefined`.
