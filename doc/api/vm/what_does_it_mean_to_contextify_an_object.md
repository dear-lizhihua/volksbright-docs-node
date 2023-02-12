## What does it mean to "contextify" an object?

All JavaScript executed within Node.js runs within the scope of a "context".
According to the [V8 Embedder's Guide][]:

> In V8, a context is an execution environment that allows separate, unrelated,
> JavaScript applications to run in a single instance of V8. You must explicitly
> specify the context in which you want any JavaScript code to be run.

When the method `vm.createContext()` is called, the `contextObject` argument
(or a newly-created object if `contextObject` is `undefined`) is associated
internally with a new instance of a V8 Context. This V8 Context provides the
`code` run using the `node:vm` module's methods with an isolated global
environment within which it can operate. The process of creating the V8 Context
and associating it with the `contextObject` is what this document refers to as
"contextifying" the object.
