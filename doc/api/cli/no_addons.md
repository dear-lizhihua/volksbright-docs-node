### `--no-addons`

<!-- YAML
added:
  - v16.10.0
  - v14.19.0
-->

Disable the `node-addons` exports condition as well as disable loading
native addons. When `--no-addons` is specified, calling `process.dlopen` or
requiring a native C++ addon will fail and throw an exception.
