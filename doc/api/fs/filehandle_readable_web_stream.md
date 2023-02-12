#### `filehandle.readableWebStream()`

<!-- YAML
added: v17.0.0
-->

> Stability: 1 - Experimental

* Returns: {ReadableStream}

Returns a `ReadableStream` that may be used to read the files data.

An error will be thrown if this method is called more than once or is called
after the `FileHandle` is closed or closing.

```mjs
import {
  open,
} from 'node:fs/promises';

const file = await open('./some/file/to/read');

for await (const chunk of file.readableWebStream())
  console.log(chunk);

await file.close();
```

```cjs
const {
  open,
} = require('node:fs/promises');

(async () => {
  const file = await open('./some/file/to/read');

  for await (const chunk of file.readableWebStream())
    console.log(chunk);

  await file.close();
})();
```

While the `ReadableStream` will read the file to completion, it will not
close the `FileHandle` automatically. User code must still call the
`fileHandle.close()` method.
