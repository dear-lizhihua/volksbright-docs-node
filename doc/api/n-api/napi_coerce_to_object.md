### `napi_coerce_to_object`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_coerce_to_object(napi_env env,
                                  napi_value value,
                                  napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: The JavaScript value to coerce.
* `[out] result`: `napi_value` representing the coerced JavaScript `Object`.

Returns `napi_ok` if the API succeeded.

This API implements the abstract operation `ToObject()` as defined in
[Section 7.1.13][] of the ECMAScript Language Specification.
