#### Event: `'end'`

The [`'end'`][] event is from the `stream.Readable` class. The `'end'` event is
emitted after all data has been output, which occurs after the callback in
[`transform._flush()`][stream-_flush] has been called. In the case of an error,
`'end'` should not be emitted.
