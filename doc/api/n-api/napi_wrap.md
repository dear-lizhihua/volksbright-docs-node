### `napi_wrap`

<!-- YAML
added: v8.0.0
napiVersion: 1
-->

```c
napi_status napi_wrap(napi_env env,
                      napi_value js_object,
                      void* native_object,
                      napi_finalize finalize_cb,
                      void* finalize_hint,
                      napi_ref* result);
```

* `[in] env`: The environment that the API is invoked under.
* `[in] js_object`: The JavaScript object that will be the wrapper for the
  native object.
* `[in] native_object`: The native instance that will be wrapped in the
  JavaScript object.
* `[in] finalize_cb`: Optional native callback that can be used to free the
  native instance when the JavaScript object has been garbage-collected.
  [`napi_finalize`][] provides more details.
* `[in] finalize_hint`: Optional contextual hint that is passed to the
  finalize callback.
* `[out] result`: Optional reference to the wrapped object.

Returns `napi_ok` if the API succeeded.

Wraps a native instance in a JavaScript object. The native instance can be
retrieved later using `napi_unwrap()`.

When JavaScript code invokes a constructor for a class that was defined using
`napi_define_class()`, the `napi_callback` for the constructor is invoked.
After constructing an instance of the native class, the callback must then call
`napi_wrap()` to wrap the newly constructed instance in the already-created
JavaScript object that is the `this` argument to the constructor callback.
(That `this` object was created from the constructor function's `prototype`,
so it already has definitions of all the instance properties and methods.)

Typically when wrapping a class instance, a finalize callback should be
provided that simply deletes the native instance that is received as the `data`
argument to the finalize callback.

The optional returned reference is initially a weak reference, meaning it
has a reference count of 0. Typically this reference count would be incremented
temporarily during async operations that require the instance to remain valid.

_Caution_: The optional returned reference (if obtained) should be deleted via
[`napi_delete_reference`][] ONLY in response to the finalize callback
invocation. If it is deleted before then, then the finalize callback may never
be invoked. Therefore, when obtaining a reference a finalize callback is also
required in order to enable correct disposal of the reference.

Finalizer callbacks may be deferred, leaving a window where the object has
been garbage collected (and the weak reference is invalid) but the finalizer
hasn't been called yet. When using `napi_get_reference_value()` on weak
references returned by `napi_wrap()`, you should still handle an empty result.

Calling `napi_wrap()` a second time on an object will return an error. To
associate another native instance with the object, use `napi_remove_wrap()`
first.
