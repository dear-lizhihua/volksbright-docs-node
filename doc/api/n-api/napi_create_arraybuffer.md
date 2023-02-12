#### `napi_create_arraybuffer`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_create_arraybuffer(napi_env env,
                                    size_t byte_length,
                                    void** data,
                                    napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] length`: The length in bytes of the array buffer to create.
* `[out] data`: Pointer to the underlying byte buffer of the `ArrayBuffer`.
  `data` can optionally be ignored by passing `NULL`.
* `[out] result`: A `napi_value` representing a JavaScript `ArrayBuffer`.

Returns `napi_ok` if the API succeeded.

This API returns a Node-API value corresponding to a JavaScript `ArrayBuffer`.
`ArrayBuffer`s are used to represent fixed-length binary data buffers. They are
normally used as a backing-buffer for `TypedArray` objects.
The `ArrayBuffer` allocated will have an underlying byte buffer whose size is
determined by the `length` parameter that's passed in.
The underlying buffer is optionally returned back to the caller in case the
caller wants to directly manipulate the buffer. This buffer can only be
written to directly from native code. To write to this buffer from JavaScript,
a typed array or `DataView` object would need to be created.

JavaScript `ArrayBuffer` objects are described in
[Section 24.1][] of the ECMAScript Language Specification.
