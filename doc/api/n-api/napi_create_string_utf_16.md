#### `napi_create_string_utf16`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_create_string_utf16(napi_env env,
                                     const char16_t* str,
                                     size_t length,
                                     napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] str`: Character buffer representing a UTF16-LE-encoded string.
* `[in] length`: The length of the string in two-byte code units, or
  `NAPI_AUTO_LENGTH` if it is null-terminated.
* `[out] result`: A `napi_value` representing a JavaScript `string`.

Returns `napi_ok` if the API succeeded.

This API creates a JavaScript `string` value from a UTF16-LE-encoded C string.
The native string is copied.

The JavaScript `string` type is described in
[Section 6.1.4][] of the ECMAScript Language Specification.
