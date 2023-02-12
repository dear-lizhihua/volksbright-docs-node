## Class: `REPLServer`

<!-- YAML
added: v0.1.91
-->

* `options` {Object|string} See [`repl.start()`][]
* Extends: {readline.Interface}

Instances of `repl.REPLServer` are created using the [`repl.start()`][] method
or directly using the JavaScript `new` keyword.

```js
const repl = require('node:repl');

const options = { useColors: true };

const firstInstance = repl.start(options);
const secondInstance = new repl.REPLServer(options);
```
