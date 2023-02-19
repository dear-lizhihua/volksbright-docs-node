##### Event: `'finish'`

<!-- YAML
added: v0.9.4
-->

The `'finish'` event is emitted after the [`stream.end()`][stream-end] method
has been called, and all data has been flushed to the underlying system.

```js
const writer = getWritableStreamSomehow();
for (let i = 0; i < 100; i++) {
  writer.write(`hello, #${i}!\n`);
}
writer.on('finish', () => {
  console.log('All writes are now complete.');
});
writer.end('This is the end\n');
```
