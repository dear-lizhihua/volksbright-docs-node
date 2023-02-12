### `module.link(linker)`

* `linker` {Function}
  * `specifier` {string} The specifier of the requested module:
    ```mjs
    import foo from 'foo';
    //              ^^^^^ the module specifier
    ```

  * `referencingModule` {vm.Module} The `Module` object `link()` is called on.

  * `extra` {Object}
    * `assert` {Object} The data from the assertion:
      <!-- eslint-skip -->
      ```js
      import foo from 'foo' assert { name: 'value' };
      //                           ^^^^^^^^^^^^^^^^^ the assertion
      ```
      Per ECMA-262, hosts are expected to ignore assertions that they do not
      support, as opposed to, for example, triggering an error if an
      unsupported assertion is present.

  * Returns: {vm.Module|Promise}
* Returns: {Promise}

Link module dependencies. This method must be called before evaluation, and
can only be called once per module.

The function is expected to return a `Module` object or a `Promise` that
eventually resolves to a `Module` object. The returned `Module` must satisfy the
following two invariants:

* It must belong to the same context as the parent `Module`.
* Its `status` must not be `'errored'`.

If the returned `Module`'s `status` is `'unlinked'`, this method will be
recursively called on the returned `Module` with the same provided `linker`
function.

`link()` returns a `Promise` that will either get resolved when all linking
instances resolve to a valid `Module`, or rejected if the linker function either
throws an exception or returns an invalid `Module`.

The linker function roughly corresponds to the implementation-defined
[HostResolveImportedModule][] abstract operation in the ECMAScript
specification, with a few key differences:

* The linker function is allowed to be asynchronous while
  [HostResolveImportedModule][] is synchronous.

The actual [HostResolveImportedModule][] implementation used during module
linking is one that returns the modules linked during linking. Since at
that point all modules would have been fully linked already, the
[HostResolveImportedModule][] implementation is fully synchronous per
specification.

Corresponds to the [Link() concrete method][] field of [Cyclic Module
Record][]s in the ECMAScript specification.
