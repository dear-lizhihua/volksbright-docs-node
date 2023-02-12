#### Async Iteration

The {ReadableStream} object supports the async iterator protocol using
`for await` syntax.

```mjs
import { Buffer } from 'node:buffer';

const stream = new ReadableStream(getSomeSource());

for await (const chunk of stream)
  console.log(Buffer.from(chunk).toString());
```

The async iterator will consume the {ReadableStream} until it terminates.

By default, if the async iterator exits early (via either a `break`,
`return`, or a `throw`), the {ReadableStream} will be closed. To prevent
automatic closing of the {ReadableStream}, use the `readableStream.values()`
method to acquire the async iterator and set the `preventCancel` option to
`true`.

The {ReadableStream} must not be locked (that is, it must not have an existing
active reader). During the async iteration, the {ReadableStream} will be locked.
