#### `napi_has_element`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_has_element(napi_env env,
                             napi_value object,
                             uint32_t index,
                             bool* result);
```

* `[in] env`: The environment that the Node-API call is invoked under.
* `[in] object`: The object to query.
* `[in] index`: The index of the property whose existence to check.
* `[out] result`: Whether the property exists on the object or not.

Returns `napi_ok` if the API succeeded.

This API returns if the `Object` passed in has an element at the
requested index.
