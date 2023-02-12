### `--import=module`

<!-- YAML
added: v19.0.0
-->

> Stability: 1 - Experimental

Preload the specified module at startup.

Follows [ECMAScript module][] resolution rules.
Use [`--require`][] to load a [CommonJS module][].
Modules preloaded with `--require` will run before modules preloaded with `--import`.
