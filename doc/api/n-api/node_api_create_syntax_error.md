#### `node_api_create_syntax_error`

<!-- YAML
added:
  - v17.2.0
  - v16.14.0
-->

> Stability: 1 - Experimental

```c
NAPI_EXTERN napi_status node_api_create_syntax_error(napi_env env,
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

This API returns a JavaScript `SyntaxError` with the text provided.
