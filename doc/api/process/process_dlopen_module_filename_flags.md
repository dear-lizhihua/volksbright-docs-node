## `process.dlopen(module, filename[, flags])`

<!-- YAML
added: v0.1.16
changes:
  - version: v9.0.0
    pr-url: https://github.com/nodejs/node/pull/12794
    description: Added support for the `flags` argument.
-->

* `module` {Object}
* `filename` {string}
* `flags` {os.constants.dlopen} **Default:** `os.constants.dlopen.RTLD_LAZY`

The `process.dlopen()` method allows dynamically loading shared objects. It is
primarily used by `require()` to load C++ Addons, and should not be used
directly, except in special cases. In other words, [`require()`][] should be
preferred over `process.dlopen()` unless there are specific reasons such as
custom dlopen flags or loading from ES modules.

The `flags` argument is an integer that allows to specify dlopen
behavior. See the [`os.constants.dlopen`][] documentation for details.

An important requirement when calling `process.dlopen()` is that the `module`
instance must be passed. Functions exported by the C++ Addon are then
accessible via `module.exports`.

The example below shows how to load a C++ Addon, named `local.node`,
that exports a `foo` function. All the symbols are loaded before
the call returns, by passing the `RTLD_NOW` constant. In this example
the constant is assumed to be available.

```mjs
import { dlopen } from 'node:process';
import { constants } from 'node:os';
import { fileURLToPath } from 'node:url';

const module = { exports: {} };
dlopen(module, fileURLToPath(new URL('local.node', import.meta.url)),
       constants.dlopen.RTLD_NOW);
module.exports.foo();
```

```cjs
const { dlopen } = require('node:process');
const { constants } = require('node:os');
const { join } = require('node:path');

const module = { exports: {} };
dlopen(module, join(__dirname, 'local.node'), constants.dlopen.RTLD_NOW);
module.exports.foo();
```
