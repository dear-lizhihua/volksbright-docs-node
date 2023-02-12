##### Event: `'unpipe'`

<!-- YAML
added: v0.9.4
-->

* `src` {stream.Readable} The source stream that
  [unpiped][`stream.unpipe()`] this writable

The `'unpipe'` event is emitted when the [`stream.unpipe()`][] method is called
on a [`Readable`][] stream, removing this [`Writable`][] from its set of
destinations.

This is also emitted in case this [`Writable`][] stream emits an error when a
[`Readable`][] stream pipes into it.

```js
const writer = getWritableStreamSomehow();
const reader = getReadableStreamSomehow();
writer.on('unpipe', (src) => {
  console.log('Something has stopped piping into the writer.');
  assert.equal(src, reader);
});
reader.pipe(writer);
reader.unpipe(writer);
```
