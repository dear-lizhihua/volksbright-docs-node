#### `napi_get_dataview_info`

<!-- YAML
added: v8.3.0
napiVersion: 1
-->

```c
napi_status napi_get_dataview_info(napi_env env,
                                   napi_value dataview,
                                   size_t* byte_length,
                                   void** data,
                                   napi_value* arraybuffer,
                                   size_t* byte_offset)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] dataview`: `napi_value` representing the `DataView` whose
  properties to query.
* `[out] byte_length`: Number of bytes in the `DataView`.
* `[out] data`: The data buffer underlying the `DataView`.
  If byte\_length is `0`, this may be `NULL` or any other pointer value.
* `[out] arraybuffer`: `ArrayBuffer` underlying the `DataView`.
* `[out] byte_offset`: The byte offset within the data buffer from which
  to start projecting the `DataView`.

Returns `napi_ok` if the API succeeded.

Any of the out parameters may be `NULL` if that property is unneeded.

This API returns various properties of a `DataView`.
