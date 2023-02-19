## Threadpool usage and performance considerations

All `zlib` APIs, except those that are explicitly synchronous, use the Node.js
internal threadpool. This can lead to surprising effects and performance
limitations in some applications.

Creating and using a large number of zlib objects simultaneously can cause
significant memory fragmentation.

```js
const zlib = require('node:zlib');

const payload = Buffer.from('This is some data');

// WARNING: DO NOT DO THIS!
for (let i = 0; i < 30000; ++i) {
  zlib.deflate(payload, (err, buffer) => {});
}
```

In the preceding example, 30,000 deflate instances are created concurrently.
Because of how some operating systems handle memory allocation and
deallocation, this may lead to significant memory fragmentation.

It is strongly recommended that the results of compression
operations be cached to avoid duplication of effort.
