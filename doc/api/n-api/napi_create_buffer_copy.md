#### `napi_create_buffer_copy`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_create_buffer_copy(napi_env env,
                                    size_t length,
                                    const void* data,
                                    void** result_data,
                                    napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] size`: Size in bytes of the input buffer (should be the same as the size
  of the new buffer).
* `[in] data`: Raw pointer to the underlying buffer to copy from.
* `[out] result_data`: Pointer to the new `Buffer`'s underlying data buffer.
  `result_data` can optionally be ignored by passing `NULL`.
* `[out] result`: A `napi_value` representing a `node::Buffer`.

Returns `napi_ok` if the API succeeded.

This API allocates a `node::Buffer` object and initializes it with data copied
from the passed-in buffer. While this is still a fully-supported data
structure, in most cases using a `TypedArray` will suffice.
