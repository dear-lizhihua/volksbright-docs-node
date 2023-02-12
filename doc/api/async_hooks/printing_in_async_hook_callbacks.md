### Printing in `AsyncHook` callbacks

Because printing to the console is an asynchronous operation, `console.log()`
will cause `AsyncHook` callbacks to be called. Using `console.log()` or
similar asynchronous operations inside an `AsyncHook` callback function will
cause an infinite recursion. An easy solution to this when debugging is to use a
synchronous logging operation such as `fs.writeFileSync(file, msg, flag)`.
This will print to the file and will not invoke `AsyncHook` recursively because
it is synchronous.

```mjs
import { writeFileSync } from 'node:fs';
import { format } from 'node:util';

function debug(...args) {
  // Use a function like this one when debugging inside an AsyncHook callback
  writeFileSync('log.out', `${format(...args)}\n`, { flag: 'a' });
}
```

```cjs
const fs = require('node:fs');
const util = require('node:util');

function debug(...args) {
  // Use a function like this one when debugging inside an AsyncHook callback
  fs.writeFileSync('log.out', `${util.format(...args)}\n`, { flag: 'a' });
}
```

If an asynchronous operation is needed for logging, it is possible to keep
track of what caused the asynchronous operation using the information
provided by `AsyncHook` itself. The logging should then be skipped when
it was the logging itself that caused the `AsyncHook` callback to be called. By
doing this, the otherwise infinite recursion is broken.
