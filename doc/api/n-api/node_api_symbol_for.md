#### `node_api_symbol_for`

<!-- YAML
added:
  - v17.5.0
  - v16.15.0
-->

> Stability: 1 - Experimental

```c
napi_status node_api_symbol_for(napi_env env,
                                const char* utf8description,
                                size_t length,
                                napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] utf8description`: UTF-8 C string representing the text to be used as the
  description for the symbol.
* `[in] length`: The length of the description string in bytes, or
  `NAPI_AUTO_LENGTH` if it is null-terminated.
* `[out] result`: A `napi_value` representing a JavaScript `symbol`.

Returns `napi_ok` if the API succeeded.

This API searches in the global registry for an existing symbol with the given
description. If the symbol already exists it will be returned, otherwise a new
symbol will be created in the registry.

The JavaScript `symbol` type is described in [Section 19.4][] of the ECMAScript
Language Specification.
