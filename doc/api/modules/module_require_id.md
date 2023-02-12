### `module.require(id)`

<!-- YAML
added: v0.5.1
-->

* `id` {string}
* Returns: {any} exported module content

The `module.require()` method provides a way to load a module as if
`require()` was called from the original module.

In order to do this, it is necessary to get a reference to the `module` object.
Since `require()` returns the `module.exports`, and the `module` is typically
_only_ available within a specific module's code, it must be explicitly exported
in order to be used.
