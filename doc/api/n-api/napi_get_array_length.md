#### `napi_get_array_length`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_get_array_length(napi_env env,
                                  napi_value value,
                                  uint32_t* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: `napi_value` representing the JavaScript `Array` whose length is
  being queried.
* `[out] result`: `uint32` representing length of the array.

Returns `napi_ok` if the API succeeded.

This API returns the length of an array.

`Array` length is described in [Section 22.1.4.1][] of the ECMAScript Language
Specification.
