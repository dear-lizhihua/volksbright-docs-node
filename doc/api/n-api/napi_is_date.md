### `napi_is_date`

<!-- YAML
added:
 - v11.11.0
 - v10.17.0
napiVersion: 5
-->

```c
napi_status napi_is_date(napi_env env, napi_value value, bool* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: The JavaScript value to check.
* `[out] result`: Whether the given `napi_value` represents a JavaScript `Date`
  object.

Returns `napi_ok` if the API succeeded.

This API checks if the `Object` passed in is a date.
