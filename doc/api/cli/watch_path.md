### `--watch-path`

<!-- YAML
added:
  - v18.11.0
  - v16.19.0
-->

> Stability: 1 - Experimental

Starts Node.js in watch mode and specifies what paths to watch.
When in watch mode, changes in the watched paths cause the Node.js process to
restart.
This will turn off watching of required or imported modules, even when used in
combination with `--watch`.

This flag cannot be combined with
`--check`, `--eval`, `--interactive`, `--test`, or the REPL.

```console
$ node --watch-path=./src --watch-path=./tests index.js
```

This option is only supported on macOS and Windows.
An `ERR_FEATURE_UNAVAILABLE_ON_PLATFORM` exception will be thrown
when the option is used on a platform that does not support it.
