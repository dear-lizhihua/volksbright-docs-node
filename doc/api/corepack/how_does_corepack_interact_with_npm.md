### How does Corepack interact with npm?

While Corepack could support npm like any other package manager, its
shims aren't enabled by default. This has a few consequences:

* It's always possible to run a `npm` command within a project configured to
  be used with another package manager, since Corepack cannot intercept it.

* While `npm` is a valid option in the [`"packageManager"`][] property, the
  lack of shim will cause the global npm to be used.
