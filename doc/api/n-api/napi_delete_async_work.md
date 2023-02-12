### `napi_delete_async_work`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_delete_async_work(napi_env env,
                                   napi_async_work work);
```

* `[in] env`: The environment that the API is invoked under.
* `[in] work`: The handle returned by the call to `napi_create_async_work`.

Returns `napi_ok` if the API succeeded.

This API frees a previously allocated work object.

This API can be called even if there is a pending JavaScript exception.
