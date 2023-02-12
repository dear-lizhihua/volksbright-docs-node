#### `napi_create_int64`

<!-- YAML
added: v8.4.0
napiVersion: 1
-->

```c
napi_status napi_create_int64(napi_env env, int64_t value, napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: Integer value to be represented in JavaScript.
* `[out] result`: A `napi_value` representing a JavaScript `number`.

Returns `napi_ok` if the API succeeded.

This API is used to convert from the C `int64_t` type to the JavaScript
`number` type.

The JavaScript `number` type is described in [Section 6.1.6][]
of the ECMAScript Language Specification. Note the complete range of `int64_t`
cannot be represented with full precision in JavaScript. Integer values
outside the range of [`Number.MIN_SAFE_INTEGER`][] `-(2**53 - 1)` -
[`Number.MAX_SAFE_INTEGER`][] `(2**53 - 1)` will lose precision.
