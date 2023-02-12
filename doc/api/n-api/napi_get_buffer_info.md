#### `napi_get_buffer_info`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_get_buffer_info(napi_env env,
                                 napi_value value,
                                 void** data,
                                 size_t* length)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: `napi_value` representing the `node::Buffer` being queried.
* `[out] data`: The underlying data buffer of the `node::Buffer`.
  If length is `0`, this may be `NULL` or any other pointer value.
* `[out] length`: Length in bytes of the underlying data buffer.

Returns `napi_ok` if the API succeeded.

This API is used to retrieve the underlying data buffer of a `node::Buffer`
and its length.

_Warning_: Use caution while using this API since the underlying data buffer's
lifetime is not guaranteed if it's managed by the VM.
