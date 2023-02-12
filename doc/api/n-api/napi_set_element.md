#### `napi_set_element`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_set_element(napi_env env,
                             napi_value object,
                             uint32_t index,
                             napi_value value);
```

* `[in] env`: The environment that the Node-API call is invoked under.
* `[in] object`: The object from which to set the properties.
* `[in] index`: The index of the property to set.
* `[in] value`: The property value.

Returns `napi_ok` if the API succeeded.

This API sets an element on the `Object` passed in.
