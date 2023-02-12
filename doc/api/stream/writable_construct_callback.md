#### `writable._construct(callback)`

<!-- YAML
added: v15.0.0
-->

* `callback` {Function} Call this function (optionally with an error
  argument) when the stream has finished initializing.

The `_construct()` method MUST NOT be called directly. It may be implemented
by child classes, and if so, will be called by the internal `Writable`
class methods only.

This optional function will be called in a tick after the stream constructor
has returned, delaying any `_write()`, `_final()` and `_destroy()` calls until
`callback` is called. This is useful to initialize state or asynchronously
initialize resources before the stream can be used.

```js
const { Writable } = require('node:stream');
const fs = require('node:fs');

class WriteStream extends Writable {
  constructor(filename) {
    super();
    this.filename = filename;
    this.fd = null;
  }
  _construct(callback) {
    fs.open(this.filename, (err, fd) => {
      if (err) {
        callback(err);
      } else {
        this.fd = fd;
        callback();
      }
    });
  }
  _write(chunk, encoding, callback) {
    fs.write(this.fd, chunk, callback);
  }
  _destroy(err, callback) {
    if (this.fd) {
      fs.close(this.fd, (er) => callback(er || err));
    } else {
      callback(err);
    }
  }
}
```
