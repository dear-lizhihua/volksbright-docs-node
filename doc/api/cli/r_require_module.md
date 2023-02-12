### `-r`, `--require module`

<!-- YAML
added: v1.6.0
-->

Preload the specified module at startup.

Follows `require()`'s module resolution
rules. `module` may be either a path to a file, or a node module name.

Only CommonJS modules are supported.
Use [`--import`][] to preload an [ECMAScript module][].
Modules preloaded with `--require` will run before modules preloaded with `--import`.
