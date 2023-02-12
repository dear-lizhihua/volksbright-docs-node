#### `readableStreamBYOBReader.read(view)`

<!-- YAML
added: v16.5.0
-->

* `view` {Buffer|TypedArray|DataView}
* Returns: A promise fulfilled with an object:
  * `value` {ArrayBuffer}
  * `done` {boolean}

Requests the next chunk of data from the underlying {ReadableStream}
and returns a promise that is fulfilled with the data once it is
available.

Do not pass a pooled {Buffer} object instance in to this method.
Pooled `Buffer` objects are created using `Buffer.allocUnsafe()`,
or `Buffer.from()`, or are often returned by various `node:fs` module
callbacks. These types of `Buffer`s use a shared underlying
{ArrayBuffer} object that contains all of the data from all of
the pooled `Buffer` instances. When a `Buffer`, {TypedArray},
or {DataView} is passed in to `readableStreamBYOBReader.read()`,
the view's underlying `ArrayBuffer` is _detached_, invalidating
all existing views that may exist on that `ArrayBuffer`. This
can have disastrous consequences for your application.
