#### `napi_has_own_property`

<!-- YAML
added: v8.2.0
napiVersion: 1
-->

```c
napi_status napi_has_own_property(napi_env env,
                                  napi_value object,
                                  napi_value key,
                                  bool* result);
```

* `[in] env`: The environment that the Node-API call is invoked under.
* `[in] object`: The object to query.
* `[in] key`: The name of the own property whose existence to check.
* `[out] result`: Whether the own property exists on the object or not.

Returns `napi_ok` if the API succeeded.

This API checks if the `Object` passed in has the named own property. `key` must
be a `string` or a `symbol`, or an error will be thrown. Node-API will not
perform any conversion between data types.
