#### `napi_has_property`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_has_property(napi_env env,
                              napi_value object,
                              napi_value key,
                              bool* result);
```

* `[in] env`: The environment that the Node-API call is invoked under.
* `[in] object`: The object to query.
* `[in] key`: The name of the property whose existence to check.
* `[out] result`: Whether the property exists on the object or not.

Returns `napi_ok` if the API succeeded.

This API checks if the `Object` passed in has the named property.
