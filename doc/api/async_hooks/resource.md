##### `resource`

`resource` is an object that represents the actual async resource that has
been initialized. The API to access the object may be specified by the
creator of the resource. Resources created by Node.js itself are internal
and may change at any time. Therefore no API is specified for these.

In some cases the resource object is reused for performance reasons, it is
thus not safe to use it as a key in a `WeakMap` or add properties to it.
