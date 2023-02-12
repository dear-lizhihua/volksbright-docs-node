#### `napi_create_symbol`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_create_symbol(napi_env env,
                               napi_value description,
                               napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] description`: Optional `napi_value` which refers to a JavaScript
  `string` to be set as the description for the symbol.
* `[out] result`: A `napi_value` representing a JavaScript `symbol`.

Returns `napi_ok` if the API succeeded.

This API creates a JavaScript `symbol` value from a UTF8-encoded C string.

The JavaScript `symbol` type is described in [Section 19.4][]
of the ECMAScript Language Specification.
