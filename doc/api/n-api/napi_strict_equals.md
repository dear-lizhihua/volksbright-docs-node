### `napi_strict_equals`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_strict_equals(napi_env env,
                               napi_value lhs,
                               napi_value rhs,
                               bool* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] lhs`: The JavaScript value to check.
* `[in] rhs`: The JavaScript value to check against.
* `[out] result`: Whether the two `napi_value` objects are equal.

Returns `napi_ok` if the API succeeded.

This API represents the invocation of the Strict Equality algorithm as
defined in [Section 7.2.14][] of the ECMAScript Language Specification.
