### `napi_make_callback`

<!-- YAML
added: v8.0.0
napiVersion: 1
changes:
  - version: v8.6.0
    pr-url: https://github.com/nodejs/node/pull/15189
    description: Added `async_context` parameter.
-->

```c
NAPI_EXTERN napi_status napi_make_callback(napi_env env,
                                           napi_async_context async_context,
                                           napi_value recv,
                                           napi_value func,
                                           size_t argc,
                                           const napi_value* argv,
                                           napi_value* result);
```

* `[in] env`: The environment that the API is invoked under.
* `[in] async_context`: Context for the async operation that is
  invoking the callback. This should normally be a value previously
  obtained from [`napi_async_init`][].
  In order to retain ABI compatibility with previous versions, passing `NULL`
  for `async_context` does not result in an error. However, this results
  in incorrect operation of async hooks. Potential issues include loss of
  async context when using the `AsyncLocalStorage` API.
* `[in] recv`: The `this` value passed to the called function.
* `[in] func`: `napi_value` representing the JavaScript function to be invoked.
* `[in] argc`: The count of elements in the `argv` array.
* `[in] argv`: Array of JavaScript values as `napi_value` representing the
  arguments to the function. If `argc` is zero this parameter may be
  omitted by passing in `NULL`.
* `[out] result`: `napi_value` representing the JavaScript object returned.

Returns `napi_ok` if the API succeeded.

This method allows a JavaScript function object to be called from a native
add-on. This API is similar to `napi_call_function`. However, it is used to call
_from_ native code back _into_ JavaScript _after_ returning from an async
operation (when there is no other script on the stack). It is a fairly simple
wrapper around `node::MakeCallback`.

Note it is _not_ necessary to use `napi_make_callback` from within a
`napi_async_complete_callback`; in that situation the callback's async
context has already been set up, so a direct call to `napi_call_function`
is sufficient and appropriate. Use of the `napi_make_callback` function
may be required when implementing custom async behavior that does not use
`napi_create_async_work`.

Any `process.nextTick`s or Promises scheduled on the microtask queue by
JavaScript during the callback are ran before returning back to C/C++.
