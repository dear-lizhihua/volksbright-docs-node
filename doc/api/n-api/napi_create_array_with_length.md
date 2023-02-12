#### `napi_create_array_with_length`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_create_array_with_length(napi_env env,
                                          size_t length,
                                          napi_value* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] length`: The initial length of the `Array`.
* `[out] result`: A `napi_value` representing a JavaScript `Array`.

Returns `napi_ok` if the API succeeded.

This API returns a Node-API value corresponding to a JavaScript `Array` type.
The `Array`'s length property is set to the passed-in length parameter.
However, the underlying buffer is not guaranteed to be pre-allocated by the VM
when the array is created. That behavior is left to the underlying VM
implementation. If the buffer must be a contiguous block of memory that can be
directly read and/or written via C, consider using
[`napi_create_external_arraybuffer`][].

JavaScript arrays are described in
[Section 22.1][] of the ECMAScript Language Specification.
