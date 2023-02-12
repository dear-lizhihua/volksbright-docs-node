### Building

Once the source code has been written, it must be compiled into the binary
`addon.node` file. To do so, create a file called `binding.gyp` in the
top-level of the project describing the build configuration of the module
using a JSON-like format. This file is used by [node-gyp][], a tool written
specifically to compile Node.js addons.

```json
{
  "targets": [
    {
      "target_name": "addon",
      "sources": [ "hello.cc" ]
    }
  ]
}
```

A version of the `node-gyp` utility is bundled and distributed with
Node.js as part of `npm`. This version is not made directly available for
developers to use and is intended only to support the ability to use the
`npm install` command to compile and install addons. Developers who wish to
use `node-gyp` directly can install it using the command
`npm install -g node-gyp`. See the `node-gyp` [installation instructions][] for
more information, including platform-specific requirements.

Once the `binding.gyp` file has been created, use `node-gyp configure` to
generate the appropriate project build files for the current platform. This
will generate either a `Makefile` (on Unix platforms) or a `vcxproj` file
(on Windows) in the `build/` directory.

Next, invoke the `node-gyp build` command to generate the compiled `addon.node`
file. This will be put into the `build/Release/` directory.

When using `npm install` to install a Node.js addon, npm uses its own bundled
version of `node-gyp` to perform this same set of actions, generating a
compiled version of the addon for the user's platform on demand.

Once built, the binary addon can be used from within Node.js by pointing
[`require()`][require] to the built `addon.node` module:

```js
// hello.js
const addon = require('./build/Release/addon');

console.log(addon.hello());
// Prints: 'world'
```

Because the exact path to the compiled addon binary can vary depending on how
it is compiled (i.e. sometimes it may be in `./build/Debug/`), addons can use
the [bindings][] package to load the compiled module.

While the `bindings` package implementation is more sophisticated in how it
locates addon modules, it is essentially using a `try…catch` pattern similar to:

```js
try {
  return require('./build/Release/addon.node');
} catch (err) {
  return require('./build/Debug/addon.node');
}
```
