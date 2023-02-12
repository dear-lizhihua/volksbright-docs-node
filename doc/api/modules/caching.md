## Caching

<!--type=misc-->

Modules are cached after the first time they are loaded. This means (among other
things) that every call to `require('foo')` will get exactly the same object
returned, if it would resolve to the same file.

Provided `require.cache` is not modified, multiple calls to `require('foo')`
will not cause the module code to be executed multiple times. This is an
important feature. With it, "partially done" objects can be returned, thus
allowing transitive dependencies to be loaded even when they would cause cycles.

To have a module execute code multiple times, export a function, and call that
function.
