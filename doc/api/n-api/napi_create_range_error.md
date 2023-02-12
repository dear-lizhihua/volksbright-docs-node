#### `napi_create_range_error`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
NAPI_EXTERN napi_status napi_create_range_error(napi_env env,
                                                napi_value code,
                                                napi_value msg,
                                                napi_value* result);
```

* `[in] env`: The environment that the API is invoked under.
* `[in] code`: Optional `napi_value` with the string for the error code to be
  associated with the error.
* `[in] msg`: `napi_value` that references a JavaScript `string` to be used as
  the message for the `Error`.
* `[out] result`: `napi_value` representing the error created.

Returns `napi_ok` if the API succeeded.

This API returns a JavaScript `RangeError` with the text provided.
