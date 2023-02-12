##### Filename argument

<!--type=misc-->

Providing `filename` argument in the callback is only supported on Linux,
macOS, Windows, and AIX. Even on supported platforms, `filename` is not always
guaranteed to be provided. Therefore, don't assume that `filename` argument is
always provided in the callback, and have some fallback logic if it is `null`.

```mjs
import { watch } from 'node:fs';
watch('somedir', (eventType, filename) => {
  console.log(`event type is: ${eventType}`);
  if (filename) {
    console.log(`filename provided: ${filename}`);
  } else {
    console.log('filename not provided');
  }
});
```
