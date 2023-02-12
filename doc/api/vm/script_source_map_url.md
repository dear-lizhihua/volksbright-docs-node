### `script.sourceMapURL`

<!-- YAML
added:
  - v19.1.0
  - v18.13.0
-->

* {string|undefined}

When the script is compiled from a source that contains a source map magic
comment, this property will be set to the URL of the source map.

```mjs
import vm from 'node:vm';

const script = new vm.Script(`
function myFunc() {}
//# sourceMappingURL=sourcemap.json
`);

console.log(script.sourceMapURL);
// Prints: sourcemap.json
```

```cjs
const vm = require('node:vm');

const script = new vm.Script(`
function myFunc() {}
//# sourceMappingURL=sourcemap.json
`);

console.log(script.sourceMapURL);
// Prints: sourcemap.json
```
