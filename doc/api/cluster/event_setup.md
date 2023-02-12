## Event: `'setup'`

<!-- YAML
added: v0.7.1
-->

* `settings` {Object}

Emitted every time [`.setupPrimary()`][] is called.

The `settings` object is the `cluster.settings` object at the time
[`.setupPrimary()`][] was called and is advisory only, since multiple calls to
[`.setupPrimary()`][] can be made in a single tick.

If accuracy is important, use `cluster.settings`.
