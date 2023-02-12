### Class: `WritableStream`

<!-- YAML
added: v16.5.0
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/42225
    description: This class is now exposed on the global object.
-->

The `WritableStream` is a destination to which stream data is sent.

```mjs
import {
  WritableStream,
} from 'node:stream/web';

const stream = new WritableStream({
  write(chunk) {
    console.log(chunk);
  },
});

await stream.getWriter().write('Hello World');
```
