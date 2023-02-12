## `process.cwd()`

<!-- YAML
added: v0.1.8
-->

* Returns: {string}

The `process.cwd()` method returns the current working directory of the Node.js
process.

```mjs
import { cwd } from 'node:process';

console.log(`Current directory: ${cwd()}`);
```

```cjs
const { cwd } = require('node:process');

console.log(`Current directory: ${cwd()}`);
```
