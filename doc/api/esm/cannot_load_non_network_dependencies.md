### Cannot load non-network dependencies

These modules cannot access other modules that are not over `http:` or `https:`.
To still access local modules while avoiding the security concern, pass in
references to the local dependencies:

```mjs
// file.mjs
import worker_threads from 'node:worker_threads';
import { configure, resize } from 'https://example.com/imagelib.mjs';
configure({ worker_threads });
```

```mjs
// https://example.com/imagelib.mjs
let worker_threads;
export function configure(opts) {
  worker_threads = opts.worker_threads;
}
export function resize(img, size) {
  // Perform resizing in worker_thread to avoid main thread blocking
}
```
