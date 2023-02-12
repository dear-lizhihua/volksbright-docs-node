##### `transform.destroy([error])`

<!-- YAML
added: v8.0.0
changes:
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/29197
    description: Work as a no-op on a stream that has already been destroyed.
-->

* `error` {Error}
* Returns: {this}

Destroy the stream, and optionally emit an `'error'` event. After this call, the
transform stream would release any internal resources.
Implementors should not override this method, but instead implement
[`readable._destroy()`][readable-_destroy].
The default implementation of `_destroy()` for `Transform` also emit `'close'`
unless `emitClose` is set in false.

Once `destroy()` has been called, any further calls will be a no-op and no
further errors except from `_destroy()` may be emitted as `'error'`.
