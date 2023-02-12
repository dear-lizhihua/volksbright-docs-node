### `napi_get_node_version`

<!-- YAML
added: v8.4.0
napiVersion: 1
-->

```c
typedef struct {
  uint32_t major;
  uint32_t minor;
  uint32_t patch;
  const char* release;
} napi_node_version;

napi_status napi_get_node_version(napi_env env,
                                  const napi_node_version** version);
```

* `[in] env`: The environment that the API is invoked under.
* `[out] version`: A pointer to version information for Node.js itself.

Returns `napi_ok` if the API succeeded.

This function fills the `version` struct with the major, minor, and patch
version of Node.js that is currently running, and the `release` field with the
value of [`process.release.name`][`process.release`].

The returned buffer is statically allocated and does not need to be freed.
