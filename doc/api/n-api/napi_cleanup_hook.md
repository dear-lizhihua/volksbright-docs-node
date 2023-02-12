#### `napi_cleanup_hook`

<!-- YAML
added:
  - v19.2.0
  - v18.13.0
napiVersion: 3
-->

Function pointer used with [`napi_add_env_cleanup_hook`][]. It will be called
when the environment is being torn down.

Callback functions must satisfy the following signature:

```c
typedef void (*napi_cleanup_hook)(void* data);
```

* `[in] data`: The data that was passed to [`napi_add_env_cleanup_hook`][].
