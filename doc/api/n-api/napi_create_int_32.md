#### `napi_create_int32`

<!-- YAML
added: v8.4.0
napiVersion: 1
-->

```c
napi_status napi_create_int32(napi_env env, int32_t value, napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: Integer value to be represented in JavaScript.
* `[out] result`: A `napi_value` representing a JavaScript `number`.

Returns `napi_ok` if the API succeeded.

This API is used to convert from the C `int32_t` type to the JavaScript
`number` type.

The JavaScript `number` type is described in
[Section 6.1.6][] of the ECMAScript Language Specification.
