#### `URL.createObjectURL(blob)`

<!-- YAML
added: v16.7.0
-->

> Stability: 1 - Experimental

* `blob` {Blob}
* Returns: {string}

Creates a `'blob:nodedata:...'` URL string that represents the given {Blob}
object and can be used to retrieve the `Blob` later.

```js
const {
  Blob,
  resolveObjectURL,
} = require('node:buffer');

const blob = new Blob(['hello']);
const id = URL.createObjectURL(blob);

// later...

const otherBlob = resolveObjectURL(id);
console.log(otherBlob.size);
```

The data stored by the registered {Blob} will be retained in memory until
`URL.revokeObjectURL()` is called to remove it.

`Blob` objects are registered within the current thread. If using Worker
Threads, `Blob` objects registered within one Worker will not be available
to other workers or the main thread.
