### `performance.toJSON()`

<!-- YAML
added: v16.1.0
changes:
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/44483
    description: This method must be called with the `performance` object as
                 the receiver.
-->

An object which is JSON representation of the `performance` object. It
is similar to [`window.performance.toJSON`][] in browsers.
