#### `napi_create_external_buffer`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_create_external_buffer(napi_env env,
                                        size_t length,
                                        void* data,
                                        napi_finalize finalize_cb,
                                        void* finalize_hint,
                                        napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] length`: Size in bytes of the input buffer (should be the same as the
  size of the new buffer).
* `[in] data`: Raw pointer to the underlying buffer to expose to JavaScript.
* `[in] finalize_cb`: Optional callback to call when the `ArrayBuffer` is being
  collected. [`napi_finalize`][] provides more details.
* `[in] finalize_hint`: Optional hint to pass to the finalize callback during
  collection.
* `[out] result`: A `napi_value` representing a `node::Buffer`.

Returns `napi_ok` if the API succeeded.

**Some runtimes other than Node.js have dropped support for external buffers**.
On runtimes other than Node.js this method may return
`napi_no_external_buffers_allowed` to indicate that external
buffers are not supported. One such runtime is Electron as
described in this issue
[electron/issues/35801](https://github.com/electron/electron/issues/35801).

In order to maintain broadest compatibility with all runtimes
you may define `NODE_API_NO_EXTERNAL_BUFFERS_ALLOWED` in your addon before
includes for the node-api headers. Doing so will hide the 2 functions
that create external buffers. This will ensure a compilation error
occurs if you accidentally use one of these methods.

This API allocates a `node::Buffer` object and initializes it with data
backed by the passed in buffer. While this is still a fully-supported data
structure, in most cases using a `TypedArray` will suffice.

The API adds a `napi_finalize` callback which will be called when the JavaScript
object just created has been garbage collected.

For Node.js >=4 `Buffers` are `Uint8Array`s.
