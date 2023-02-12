## Timeout interactions with asynchronous tasks and Promises

`Promise`s and `async function`s can schedule tasks run by the JavaScript
engine asynchronously. By default, these tasks are run after all JavaScript
functions on the current stack are done executing.
This allows escaping the functionality of the `timeout` and
`breakOnSigint` options.

For example, the following code executed by `vm.runInNewContext()` with a
timeout of 5 milliseconds schedules an infinite loop to run after a promise
resolves. The scheduled loop is never interrupted by the timeout:

```js
const vm = require('node:vm');

function loop() {
  console.log('entering loop');
  while (1) console.log(Date.now());
}

vm.runInNewContext(
  'Promise.resolve().then(() => loop());',
  { loop, console },
  { timeout: 5 },
);
// This is printed *before* 'entering loop' (!)
console.log('done executing');
```

This can be addressed by passing `microtaskMode: 'afterEvaluate'` to the code
that creates the `Context`:

```js
const vm = require('node:vm');

function loop() {
  while (1) console.log(Date.now());
}

vm.runInNewContext(
  'Promise.resolve().then(() => loop());',
  { loop, console },
  { timeout: 5, microtaskMode: 'afterEvaluate' },
);
```

In this case, the microtask scheduled through `promise.then()` will be run
before returning from `vm.runInNewContext()`, and will be interrupted
by the `timeout` functionality. This applies only to code running in a
`vm.Context`, so e.g. [`vm.runInThisContext()`][] does not take this option.

Promise callbacks are entered into the microtask queue of the context in which
they were created. For example, if `() => loop()` is replaced with just `loop`
in the above example, then `loop` will be pushed into the global microtask
queue, because it is a function from the outer (main) context, and thus will
also be able to escape the timeout.

If asynchronous scheduling functions such as `process.nextTick()`,
`queueMicrotask()`, `setTimeout()`, `setImmediate()`, etc. are made available
inside a `vm.Context`, functions passed to them will be added to global queues,
which are shared by all contexts. Therefore, callbacks passed to those functions
are not controllable through the timeout either.

[Cyclic Module Record]: https://tc39.es/ecma262/#sec-cyclic-module-records
[ECMAScript Module Loader]: esm.md#modules-ecmascript-modules
[Evaluate() concrete method]: https://tc39.es/ecma262/#sec-moduleevaluation
[GetModuleNamespace]: https://tc39.es/ecma262/#sec-getmodulenamespace
[HostResolveImportedModule]: https://tc39.es/ecma262/#sec-hostresolveimportedmodule
[Link() concrete method]: https://tc39.es/ecma262/#sec-moduledeclarationlinking
[Module Record]: https://www.ecma-international.org/ecma-262/#sec-abstract-module-records
[Source Text Module Record]: https://tc39.es/ecma262/#sec-source-text-module-records
[Synthetic Module Record]: https://heycam.github.io/webidl/#synthetic-module-records
[V8 Embedder's Guide]: https://v8.dev/docs/embed#contexts
[`ERR_VM_DYNAMIC_IMPORT_CALLBACK_MISSING`]: errors.md#err_vm_dynamic_import_callback_missing
[`ERR_VM_MODULE_STATUS`]: errors.md#err_vm_module_status
[`Error`]: errors.md#class-error
[`URL`]: url.md#class-url
[`eval()`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval
[`optionsExpression`]: https://tc39.es/proposal-import-assertions/#sec-evaluate-import-call
[`script.runInContext()`]: #scriptrunincontextcontextifiedobject-options
[`script.runInThisContext()`]: #scriptruninthiscontextoptions
[`url.origin`]: url.md#urlorigin
[`vm.createContext()`]: #vmcreatecontextcontextobject-options
[`vm.runInContext()`]: #vmrunincontextcode-contextifiedobject-options
[`vm.runInThisContext()`]: #vmruninthiscontextcode-options
[contextified]: #what-does-it-mean-to-contextify-an-object
[global object]: https://es5.github.io/#x15.1
[indirect `eval()` call]: https://es5.github.io/#x10.4.2
[origin]: https://developer.mozilla.org/en-US/docs/Glossary/Origin
