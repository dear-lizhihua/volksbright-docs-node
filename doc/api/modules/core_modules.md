## Core modules

<!--type=misc-->

<!-- YAML
changes:
  - version:
      - v16.0.0
      - v14.18.0
    pr-url: https://github.com/nodejs/node/pull/37246
    description: Added `node:` import support to `require(...)`.
-->

Node.js has several modules compiled into the binary. These modules are
described in greater detail elsewhere in this documentation.

The core modules are defined within the Node.js source and are located in the
`lib/` folder.

Core modules can be identified using the `node:` prefix, in which case
it bypasses the `require` cache. For instance, `require('node:http')` will
always return the built in HTTP module, even if there is `require.cache` entry
by that name.

Some core modules are always preferentially loaded if their identifier is
passed to `require()`. For instance, `require('http')` will always
return the built-in HTTP module, even if there is a file by that name. The list
of core modules that can be loaded without using the `node:` prefix is exposed
as [`module.builtinModules`][].
