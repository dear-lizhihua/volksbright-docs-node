### Context-aware addons

There are environments in which Node.js addons may need to be loaded multiple
times in multiple contexts. For example, the [Electron][] runtime runs multiple
instances of Node.js in a single process. Each instance will have its own
`require()` cache, and thus each instance will need a native addon to behave
correctly when loaded via `require()`. This means that the addon
must support multiple initializations.

A context-aware addon can be constructed by using the macro
`NODE_MODULE_INITIALIZER`, which expands to the name of a function which Node.js
will expect to find when it loads an addon. An addon can thus be initialized as
in the following example:

```cpp
using namespace v8;

extern "C" NODE_MODULE_EXPORT void
NODE_MODULE_INITIALIZER(Local<Object> exports,
                        Local<Value> module,
                        Local<Context> context) {
  /* Perform addon initialization steps here. */
}
```

Another option is to use the macro `NODE_MODULE_INIT()`, which will also
construct a context-aware addon. Unlike `NODE_MODULE()`, which is used to
construct an addon around a given addon initializer function,
`NODE_MODULE_INIT()` serves as the declaration of such an initializer to be
followed by a function body.

The following three variables may be used inside the function body following an
invocation of `NODE_MODULE_INIT()`:

* `Local<Object> exports`,
* `Local<Value> module`, and
* `Local<Context> context`

The choice to build a context-aware addon carries with it the responsibility of
carefully managing global static data. Since the addon may be loaded multiple
times, potentially even from different threads, any global static data stored
in the addon must be properly protected, and must not contain any persistent
references to JavaScript objects. The reason for this is that JavaScript
objects are only valid in one context, and will likely cause a crash when
accessed from the wrong context or from a different thread than the one on which
they were created.

The context-aware addon can be structured to avoid global static data by
performing the following steps:

* Define a class which will hold per-addon-instance data and which has a static
  member of the form
  ```cpp
  static void DeleteInstance(void* data) {
    // Cast `data` to an instance of the class and delete it.
  }
  ```
* Heap-allocate an instance of this class in the addon initializer. This can be
  accomplished using the `new` keyword.
* Call `node::AddEnvironmentCleanupHook()`, passing it the above-created
  instance and a pointer to `DeleteInstance()`. This will ensure the instance is
  deleted when the environment is torn down.
* Store the instance of the class in a `v8::External`, and
* Pass the `v8::External` to all methods exposed to JavaScript by passing it
  to `v8::FunctionTemplate::New()` or `v8::Function::New()` which creates the
  native-backed JavaScript functions. The third parameter of
  `v8::FunctionTemplate::New()` or `v8::Function::New()`  accepts the
  `v8::External` and makes it available in the native callback using the
  `v8::FunctionCallbackInfo::Data()` method.

This will ensure that the per-addon-instance data reaches each binding that can
be called from JavaScript. The per-addon-instance data must also be passed into
any asynchronous callbacks the addon may create.

The following example illustrates the implementation of a context-aware addon:

```cpp
#include <node.h>

using namespace v8;

class AddonData {
 public:
  explicit AddonData(Isolate* isolate):
      call_count(0) {
    // Ensure this per-addon-instance data is deleted at environment cleanup.
    node::AddEnvironmentCleanupHook(isolate, DeleteInstance, this);
  }

  // Per-addon data.
  int call_count;

  static void DeleteInstance(void* data) {
    delete static_cast<AddonData*>(data);
  }
};

static void Method(const v8::FunctionCallbackInfo<v8::Value>& info) {
  // Retrieve the per-addon-instance data.
  AddonData* data =
      reinterpret_cast<AddonData*>(info.Data().As<External>()->Value());
  data->call_count++;
  info.GetReturnValue().Set((double)data->call_count);
}

// Initialize this addon to be context-aware.
NODE_MODULE_INIT(/* exports, module, context */) {
  Isolate* isolate = context->GetIsolate();

  // Create a new instance of `AddonData` for this instance of the addon and
  // tie its life cycle to that of the Node.js environment.
  AddonData* data = new AddonData(isolate);

  // Wrap the data in a `v8::External` so we can pass it to the method we
  // expose.
  Local<External> external = External::New(isolate, data);

  // Expose the method `Method` to JavaScript, and make sure it receives the
  // per-addon-instance data we created above by passing `external` as the
  // third parameter to the `FunctionTemplate` constructor.
  exports->Set(context,
               String::NewFromUtf8(isolate, "method").ToLocalChecked(),
               FunctionTemplate::New(isolate, Method, external)
                  ->GetFunction(context).ToLocalChecked()).FromJust();
}
```
