##### `readable.wrap(stream)`

<!-- YAML
added: v0.9.4
-->

* `stream` {Stream} An "old style" readable stream
* Returns: {this}

Prior to Node.js 0.10, streams did not implement the entire `node:stream`
module API as it is currently defined. (See [Compatibility][] for more
information.)

When using an older Node.js library that emits [`'data'`][] events and has a
[`stream.pause()`][stream-pause] method that is advisory only, the
`readable.wrap()` method can be used to create a [`Readable`][] stream that uses
the old stream as its data source.

It will rarely be necessary to use `readable.wrap()` but the method has been
provided as a convenience for interacting with older Node.js applications and
libraries.

```js
const { OldReader } = require('./old-api-module.js');
const { Readable } = require('node:stream');
const oreader = new OldReader();
const myReader = new Readable().wrap(oreader);

myReader.on('readable', () => {
  myReader.read(); // etc.
});
```
