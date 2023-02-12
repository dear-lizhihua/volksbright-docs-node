#### `napi_reference_unref`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
NAPI_EXTERN napi_status napi_reference_unref(napi_env env,
                                             napi_ref ref,
                                             uint32_t* result);
```

* `[in] env`: The environment that the API is invoked under.
* `[in] ref`: `napi_ref` for which the reference count will be decremented.
* `[out] result`: The new reference count.

Returns `napi_ok` if the API succeeded.

This API decrements the reference count for the reference
passed in and returns the resulting reference count.
