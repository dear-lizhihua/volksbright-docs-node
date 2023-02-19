#### Event: `'finish'`

The [`'finish'`][] event is from the `stream.Writable` class. The `'finish'`
event is emitted after [`stream.end()`][stream-end] is called and all chunks
have been processed by [`stream._transform()`][stream-_transform]. In the case
of an error, `'finish'` should not be emitted.
