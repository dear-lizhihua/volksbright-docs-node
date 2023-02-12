##### Event: `'readable'`

<!-- YAML
added: v0.9.4
changes:
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/17979
    description: The `'readable'` is always emitted in the next tick after
                 `.push()` is called.
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18994
    description: Using `'readable'` requires calling `.read()`.
-->

The `'readable'` event is emitted when there is data available to be read from
the stream or when the end of the stream has been reached. Effectively, the
`'readable'` event indicates that the stream has new information. If data is
available, [`stream.read()`][stream-read] will return that data.

```js
const readable = getReadableStreamSomehow();
readable.on('readable', function() {
  // There is some data to read now.
  let data;

  while ((data = this.read()) !== null) {
    console.log(data);
  }
});
```

If the end of the stream has been reached, calling
[`stream.read()`][stream-read] will return `null` and trigger the `'end'`
event. This is also true if there never was any data to be read. For instance,
in the following example, `foo.txt` is an empty file:

```js
const fs = require('node:fs');
const rr = fs.createReadStream('foo.txt');
rr.on('readable', () => {
  console.log(`readable: ${rr.read()}`);
});
rr.on('end', () => {
  console.log('end');
});
```

The output of running this script is:

```console
$ node test.js
readable: null
end
```

In some cases, attaching a listener for the `'readable'` event will cause some
amount of data to be read into an internal buffer.

In general, the `readable.pipe()` and `'data'` event mechanisms are easier to
understand than the `'readable'` event. However, handling `'readable'` might
result in increased throughput.

If both `'readable'` and [`'data'`][] are used at the same time, `'readable'`
takes precedence in controlling the flow, i.e. `'data'` will be emitted
only when [`stream.read()`][stream-read] is called. The
`readableFlowing` property would become `false`.
If there are `'data'` listeners when `'readable'` is removed, the stream
will start flowing, i.e. `'data'` events will be emitted without calling
`.resume()`.
