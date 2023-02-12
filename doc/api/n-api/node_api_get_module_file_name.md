### `node_api_get_module_file_name`

<!-- YAML
added:
  - v15.9.0
  - v14.18.0
  - v12.22.0
-->

> Stability: 1 - Experimental

```c
NAPI_EXTERN napi_status
node_api_get_module_file_name(napi_env env, const char** result);

```

* `[in] env`: The environment that the API is invoked under.
* `[out] result`: A URL containing the absolute path of the
  location from which the add-on was loaded. For a file on the local
  file system it will start with `file://`. The string is null-terminated and
  owned by `env` and must thus not be modified or freed.

`result` may be an empty string if the add-on loading process fails to establish
the add-on's file name during loading.

[ABI Stability]: https://nodejs.org/en/docs/guides/abi-stability/
[AppVeyor]: https://www.appveyor.com
[C++ Addons]: addons.md
[CMake]: https://cmake.org
[CMake.js]: https://github.com/cmake-js/cmake-js
[ECMAScript Language Specification]: https://tc39.github.io/ecma262/
[Error handling]: #error-handling
[GCC]: https://gcc.gnu.org
[GYP]: https://gyp.gsrc.io
[GitHub releases]: https://help.github.com/en/github/administering-a-repository/about-releases
[LLVM]: https://llvm.org
[Native Abstractions for Node.js]: https://github.com/nodejs/nan
[Node-API Media]: https://github.com/nodejs/abi-stable-node/blob/HEAD/node-api-media.md
[Object lifetime management]: #object-lifetime-management
[Object wrap]: #object-wrap
[Section 12.10.4]: https://tc39.github.io/ecma262/#sec-instanceofoperator
[Section 12.5.5]: https://tc39.github.io/ecma262/#sec-typeof-operator
[Section 19.2]: https://tc39.github.io/ecma262/#sec-function-objects
[Section 19.4]: https://tc39.github.io/ecma262/#sec-symbol-objects
[Section 20.3]: https://tc39.github.io/ecma262/#sec-date-objects
[Section 22.1]: https://tc39.github.io/ecma262/#sec-array-objects
[Section 22.1.4.1]: https://tc39.github.io/ecma262/#sec-properties-of-array-instances-length
[Section 22.2]: https://tc39.github.io/ecma262/#sec-typedarray-objects
[Section 24.1]: https://tc39.github.io/ecma262/#sec-arraybuffer-objects
[Section 24.1.1.2]: https://tc39.es/ecma262/#sec-isdetachedbuffer
[Section 24.1.1.3]: https://tc39.es/ecma262/#sec-detacharraybuffer
[Section 24.3]: https://tc39.github.io/ecma262/#sec-dataview-objects
[Section 25.4]: https://tc39.github.io/ecma262/#sec-promise-objects
[Section 6]: https://tc39.github.io/ecma262/#sec-ecmascript-data-types-and-values
[Section 6.1]: https://tc39.github.io/ecma262/#sec-ecmascript-language-types
[Section 6.1.4]: https://tc39.github.io/ecma262/#sec-ecmascript-language-types-string-type
[Section 6.1.6]: https://tc39.github.io/ecma262/#sec-ecmascript-language-types-number-type
[Section 6.1.7]: https://tc39.github.io/ecma262/#sec-object-type
[Section 6.1.7.1]: https://tc39.github.io/ecma262/#table-2
[Section 7]: https://tc39.github.io/ecma262/#sec-abstract-operations
[Section 7.1.13]: https://tc39.github.io/ecma262/#sec-toobject
[Section 7.1.2]: https://tc39.github.io/ecma262/#sec-toboolean
[Section 7.1.3]: https://tc39.github.io/ecma262/#sec-tonumber
[Section 7.2.14]: https://tc39.github.io/ecma262/#sec-strict-equality-comparison
[Section 7.2.2]: https://tc39.github.io/ecma262/#sec-isarray
[Section 8.7]: https://tc39.es/ecma262/#sec-agents
[Section 9.1.6]: https://tc39.github.io/ecma262/#sec-ordinary-object-internal-methods-and-internal-slots-defineownproperty-p-desc
[Travis CI]: https://travis-ci.org
[Visual Studio]: https://visualstudio.microsoft.com
[Working with JavaScript properties]: #working-with-javascript-properties
[Xcode]: https://developer.apple.com/xcode/
[`Number.MAX_SAFE_INTEGER`]: https://tc39.github.io/ecma262/#sec-number.max_safe_integer
[`Number.MIN_SAFE_INTEGER`]: https://tc39.github.io/ecma262/#sec-number.min_safe_integer
[`Worker`]: worker_threads.md#class-worker
[`async_hooks.executionAsyncResource()`]: async_hooks.md#async_hooksexecutionasyncresource
[`global`]: globals.md#global
[`init` hooks]: async_hooks.md#initasyncid-type-triggerasyncid-resource
[`napi_add_async_cleanup_hook`]: #napi_add_async_cleanup_hook
[`napi_add_env_cleanup_hook`]: #napi_add_env_cleanup_hook
[`napi_add_finalizer`]: #napi_add_finalizer
[`napi_async_cleanup_hook`]: #napi_async_cleanup_hook
[`napi_async_complete_callback`]: #napi_async_complete_callback
[`napi_async_destroy`]: #napi_async_destroy
[`napi_async_init`]: #napi_async_init
[`napi_callback`]: #napi_callback
[`napi_cancel_async_work`]: #napi_cancel_async_work
[`napi_close_callback_scope`]: #napi_close_callback_scope
[`napi_close_escapable_handle_scope`]: #napi_close_escapable_handle_scope
[`napi_close_handle_scope`]: #napi_close_handle_scope
[`napi_create_async_work`]: #napi_create_async_work
[`napi_create_error`]: #napi_create_error
[`napi_create_external_arraybuffer`]: #napi_create_external_arraybuffer
[`napi_create_range_error`]: #napi_create_range_error
[`napi_create_reference`]: #napi_create_reference
[`napi_create_type_error`]: #napi_create_type_error
[`napi_define_class`]: #napi_define_class
[`napi_delete_async_work`]: #napi_delete_async_work
[`napi_delete_reference`]: #napi_delete_reference
[`napi_escape_handle`]: #napi_escape_handle
[`napi_finalize`]: #napi_finalize
[`napi_get_and_clear_last_exception`]: #napi_get_and_clear_last_exception
[`napi_get_array_length`]: #napi_get_array_length
[`napi_get_element`]: #napi_get_element
[`napi_get_last_error_info`]: #napi_get_last_error_info
[`napi_get_property`]: #napi_get_property
[`napi_get_reference_value`]: #napi_get_reference_value
[`napi_get_value_external`]: #napi_get_value_external
[`napi_has_property`]: #napi_has_property
[`napi_instanceof`]: #napi_instanceof
[`napi_is_error`]: #napi_is_error
[`napi_is_exception_pending`]: #napi_is_exception_pending
[`napi_make_callback`]: #napi_make_callback
[`napi_open_callback_scope`]: #napi_open_callback_scope
[`napi_open_escapable_handle_scope`]: #napi_open_escapable_handle_scope
[`napi_open_handle_scope`]: #napi_open_handle_scope
[`napi_property_attributes`]: #napi_property_attributes
[`napi_property_descriptor`]: #napi_property_descriptor
[`napi_queue_async_work`]: #napi_queue_async_work
[`napi_reference_ref`]: #napi_reference_ref
[`napi_reference_unref`]: #napi_reference_unref
[`napi_remove_async_cleanup_hook`]: #napi_remove_async_cleanup_hook
[`napi_remove_env_cleanup_hook`]: #napi_remove_env_cleanup_hook
[`napi_set_instance_data`]: #napi_set_instance_data
[`napi_set_property`]: #napi_set_property
[`napi_threadsafe_function_call_js`]: #napi_threadsafe_function_call_js
[`napi_throw_error`]: #napi_throw_error
[`napi_throw_range_error`]: #napi_throw_range_error
[`napi_throw_type_error`]: #napi_throw_type_error
[`napi_throw`]: #napi_throw
[`napi_unwrap`]: #napi_unwrap
[`napi_wrap`]: #napi_wrap
[`node-addon-api`]: https://github.com/nodejs/node-addon-api
[`node_api.h`]: https://github.com/nodejs/node/blob/HEAD/src/node_api.h
[`node_api_create_syntax_error`]: #node_api_create_syntax_error
[`node_api_throw_syntax_error`]: #node_api_throw_syntax_error
[`process.release`]: process.md#processrelease
[`uv_ref`]: https://docs.libuv.org/en/v1.x/handle.html#c.uv_ref
[`uv_unref`]: https://docs.libuv.org/en/v1.x/handle.html#c.uv_unref
[async_hooks `type`]: async_hooks.md#type
[context-aware addons]: addons.md#context-aware-addons
[docs]: https://github.com/nodejs/node-addon-api#api-documentation
[global scope]: globals.md
[gyp-next]: https://github.com/nodejs/gyp-next
[module scope]: modules.md#the-module-scope
[node-gyp]: https://github.com/nodejs/node-gyp
[node-pre-gyp]: https://github.com/mapbox/node-pre-gyp
[prebuild]: https://github.com/prebuild/prebuild
[prebuildify]: https://github.com/prebuild/prebuildify
[worker threads]: https://nodejs.org/api/worker_threads.html
