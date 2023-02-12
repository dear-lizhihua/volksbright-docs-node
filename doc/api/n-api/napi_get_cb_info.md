### `napi_get_cb_info`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_get_cb_info(napi_env env,
                             napi_callback_info cbinfo,
                             size_t* argc,
                             napi_value* argv,
                             napi_value* thisArg,
                             void** data)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] cbinfo`: The callback info passed into the callback function.
* `[in-out] argc`: Specifies the length of the provided `argv` array and
  receives the actual count of arguments. `argc` can
  optionally be ignored by passing `NULL`.
* `[out] argv`: C array of `napi_value`s to which the arguments will be
  copied. If there are more arguments than the provided count, only the
  requested number of arguments are copied. If there are fewer arguments
  provided than claimed, the rest of `argv` is filled with `napi_value` values
  that represent `undefined`. `argv` can optionally be ignored by
  passing `NULL`.
* `[out] thisArg`: Receives the JavaScript `this` argument for the call.
  `thisArg` can optionally be ignored by passing `NULL`.
* `[out] data`: Receives the data pointer for the callback. `data` can
  optionally be ignored by passing `NULL`.

Returns `napi_ok` if the API succeeded.

This method is used within a callback function to retrieve details about the
call like the arguments and the `this` pointer from a given callback info.
