### The `--zero-fill-buffers` command-line option

<!-- YAML
added: v5.10.0
-->

Node.js can be started using the `--zero-fill-buffers` command-line option to
cause all newly-allocated `Buffer` instances to be zero-filled upon creation by
default. Without the option, buffers created with [`Buffer.allocUnsafe()`][],
[`Buffer.allocUnsafeSlow()`][], and `new SlowBuffer(size)` are not zero-filled.
Use of this flag can have a measurable negative impact on performance. Use the
`--zero-fill-buffers` option only when necessary to enforce that newly allocated
`Buffer` instances cannot contain old data that is potentially sensitive.

```console
$ node --zero-fill-buffers
> Buffer.allocUnsafe(5);
<Buffer 00 00 00 00 00>
```
