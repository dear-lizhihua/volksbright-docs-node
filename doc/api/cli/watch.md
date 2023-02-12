### `--watch`

<!-- YAML
added:
  - v18.11.0
  - v16.19.0
changes:
  - version:
      - v19.2.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/45214
    description: Test runner now supports running in watch mode.
-->

> Stability: 1 - Experimental

Starts Node.js in watch mode.
When in watch mode, changes in the watched files cause the Node.js process to
restart.
By default, watch mode will watch the entry point
and any required or imported module.
Use `--watch-path` to specify what paths to watch.

This flag cannot be combined with
`--check`, `--eval`, `--interactive`, or the REPL.

```console
$ node --watch index.js
```
