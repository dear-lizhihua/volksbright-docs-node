#### `napi_get_value_int32`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_get_value_int32(napi_env env,
                                 napi_value value,
                                 int32_t* result)
```

* `[in] env`: The environment that the API is invoked under.
* `[in] value`: `napi_value` representing JavaScript `number`.
* `[out] result`: C `int32` primitive equivalent of the given JavaScript
  `number`.

Returns `napi_ok` if the API succeeded. If a non-number `napi_value`
is passed in `napi_number_expected`.

This API returns the C `int32` primitive equivalent
of the given JavaScript `number`.

If the number exceeds the range of the 32 bit integer, then the result is
truncated to the equivalent of the bottom 32 bits. This can result in a large
positive number becoming a negative number if the value is > 2<sup>31</sup> - 1.

Non-finite number values (`NaN`, `+Infinity`, or `-Infinity`) set the
result to zero.
