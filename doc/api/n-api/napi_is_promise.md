### `napi_is_promise`

<!-- YAML
added: v8.5.0
napiVersion: 1
-->

```c
napi_status napi_is_promise(napi_env env,
                            napi_value value,
                            bool* is_promise);
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: The value to examine
* `[out] is_promise`: Flag indicating whether `promise` is a native promise
  object (that is, a promise object created by the underlying engine).
