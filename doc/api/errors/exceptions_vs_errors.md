## Exceptions vs. errors

<!--type=misc-->

A JavaScript exception is a value that is thrown as a result of an invalid
operation or as the target of a `throw` statement. While it is not required
that these values are instances of `Error` or classes which inherit from
`Error`, all exceptions thrown by Node.js or the JavaScript runtime _will_ be
instances of `Error`.

Some exceptions are _unrecoverable_ at the JavaScript layer. Such exceptions
will _always_ cause the Node.js process to crash. Examples include `assert()`
checks or `abort()` calls in the C++ layer.
