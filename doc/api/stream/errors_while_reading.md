#### Errors while reading

Errors occurring during processing of the [`readable._read()`][] must be
propagated through the [`readable.destroy(err)`][readable-_destroy] method.
Throwing an `Error` from within [`readable._read()`][] or manually emitting an
`'error'` event results in undefined behavior.

```js
const { Readable } = require('node:stream');

const myReadable = new Readable({
  read(size) {
    const err = checkSomeErrorCondition();
    if (err) {
      this.destroy(err);
    } else {
      // Do some work.
    }
  },
});
```
