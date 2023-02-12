### `domain.run(fn[, ...args])`

* `fn` {Function}
* `...args` {any}

Run the supplied function in the context of the domain, implicitly
binding all event emitters, timers, and lowlevel requests that are
created in that context. Optionally, arguments can be passed to
the function.

This is the most basic way to use a domain.

```js
const domain = require('node:domain');
const fs = require('node:fs');
const d = domain.create();
d.on('error', (er) => {
  console.error('Caught error!', er);
});
d.run(() => {
  process.nextTick(() => {
    setTimeout(() => { // Simulating some various async stuff
      fs.open('non-existent file', 'r', (er, fd) => {
        if (er) throw er;
        // proceed...
      });
    }, 100);
  });
});
```

In this example, the `d.on('error')` handler will be triggered, rather
than crashing the program.
