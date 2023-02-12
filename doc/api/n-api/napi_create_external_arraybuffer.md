#### `napi_create_external_arraybuffer`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status
napi_create_external_arraybuffer(napi_env env,
                                 void* external_data,
                                 size_t byte_length,
                                 napi_finalize finalize_cb,
                                 void* finalize_hint,
                                 napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] external_data`: Pointer to the underlying byte buffer of the
  `ArrayBuffer`.
* `[in] byte_length`: The length in bytes of the underlying buffer.
* `[in] finalize_cb`: Optional callback to call when the `ArrayBuffer` is being
  collected. [`napi_finalize`][] provides more details.
* `[in] finalize_hint`: Optional hint to pass to the finalize callback during
  collection.
* `[out] result`: A `napi_value` representing a JavaScript `ArrayBuffer`.

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

This API returns a Node-API value corresponding to a JavaScript `ArrayBuffer`.
The underlying byte buffer of the `ArrayBuffer` is externally allocated and
managed. The caller must ensure that the byte buffer remains valid until the
finalize callback is called.

The API adds a `napi_finalize` callback which will be called when the JavaScript
object just created has been garbage collected.

JavaScript `ArrayBuffer`s are described in
[Section 24.1][] of the ECMAScript Language Specification.
