#### `napi_get_last_error_info`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status
napi_get_last_error_info(napi_env env,
                         const napi_extended_error_info** result);
```

* `[in] env`: The environment that the API is invoked under.
* `[out] result`: The `napi_extended_error_info` structure with more
  information about the error.

Returns `napi_ok` if the API succeeded.

This API retrieves a `napi_extended_error_info` structure with information
about the last error that occurred.

The content of the `napi_extended_error_info` returned is only valid up until
a Node-API function is called on the same `env`. This includes a call to
`napi_is_exception_pending` so it may often be necessary to make a copy
of the information so that it can be used later. The pointer returned
in `error_message` points to a statically-defined string so it is safe to use
that pointer if you have copied it out of the `error_message` field (which will
be overwritten) before another Node-API function was called.

Do not rely on the content or format of any of the extended information as it
is not subject to SemVer and may change at any time. It is intended only for
logging purposes.

This API can be called even if there is a pending JavaScript exception.
