### Class: `fs.Dir`

<!-- YAML
added: v12.12.0
-->

A class representing a directory stream.

Created by [`fs.opendir()`][], [`fs.opendirSync()`][], or
[`fsPromises.opendir()`][].

```mjs
import { opendir } from 'node:fs/promises';

try {
  const dir = await opendir('./');
  for await (const dirent of dir)
    console.log(dirent.name);
} catch (err) {
  console.error(err);
}
```

When using the async iterator, the {fs.Dir} object will be automatically
closed after the iterator exits.
