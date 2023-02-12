#### `napi_get_property_names`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_get_property_names(napi_env env,
                                    napi_value object,
                                    napi_value* result);
```

* `[in] env`: The environment that the Node-API call is invoked under.
* `[in] object`: The object from which to retrieve the properties.
* `[out] result`: A `napi_value` representing an array of JavaScript values
  that represent the property names of the object. The API can be used to
  iterate over `result` using [`napi_get_array_length`][]
  and [`napi_get_element`][].

Returns `napi_ok` if the API succeeded.

This API returns the names of the enumerable properties of `object` as an array
of strings. The properties of `object` whose key is a symbol will not be
included.
