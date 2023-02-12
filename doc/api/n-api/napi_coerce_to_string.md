### `napi_coerce_to_string`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_coerce_to_string(napi_env env,
                                  napi_value value,
                                  napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: The JavaScript value to coerce.
* `[out] result`: `napi_value` representing the coerced JavaScript `string`.

Returns `napi_ok` if the API succeeded.

This API implements the abstract operation `ToString()` as defined in
[Section 7.1.13][] of the ECMAScript Language Specification.
This function potentially runs JS code if the passed-in value is an
object.
