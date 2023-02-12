### `error.errno`

* {number}

The `error.errno` property is a negative number which corresponds
to the error code defined in [`libuv Error handling`][].

On Windows the error number provided by the system will be normalized by libuv.

To get the string representation of the error code, use
[`util.getSystemErrorName(error.errno)`][].
