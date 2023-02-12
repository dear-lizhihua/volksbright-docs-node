## Node-API

> Stability: 2 - Stable

Node-API is an API for building native addons. It is independent from
the underlying JavaScript runtime (e.g. V8) and is maintained as part of
Node.js itself. This API will be Application Binary Interface (ABI) stable
across versions of Node.js. It is intended to insulate addons from
changes in the underlying JavaScript engine and allow modules
compiled for one version to run on later versions of Node.js without
recompilation. Addons are built/packaged with the same approach/tools
outlined in this document (node-gyp, etc.). The only difference is the
set of APIs that are used by the native code. Instead of using the V8
or [Native Abstractions for Node.js][] APIs, the functions available
in the Node-API are used.

Creating and maintaining an addon that benefits from the ABI stability
provided by Node-API carries with it certain
[implementation considerations][].

To use Node-API in the above "Hello world" example, replace the content of
`hello.cc` with the following. All other instructions remain the same.

```cpp
// hello.cc using Node-API
#include <node_api.h>

namespace demo {

napi_value Method(napi_env env, napi_callback_info args) {
  napi_value greeting;
  napi_status status;

  status = napi_create_string_utf8(env, "world", NAPI_AUTO_LENGTH, &greeting);
  if (status != napi_ok) return nullptr;
  return greeting;
}

napi_value init(napi_env env, napi_value exports) {
  napi_status status;
  napi_value fn;

  status = napi_create_function(env, nullptr, 0, Method, nullptr, &fn);
  if (status != napi_ok) return nullptr;

  status = napi_set_named_property(env, exports, "hello", fn);
  if (status != napi_ok) return nullptr;
  return exports;
}

NAPI_MODULE(NODE_GYP_MODULE_NAME, init)

}  // namespace demo
```

The functions available and how to use them are documented in
[C/C++ addons with Node-API](n-api.md).
