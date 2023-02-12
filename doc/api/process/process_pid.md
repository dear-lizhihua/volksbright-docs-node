## `process.pid`

<!-- YAML
added: v0.1.15
-->

* {integer}

The `process.pid` property returns the PID of the process.

```mjs
import { pid } from 'node:process';

console.log(`This process is pid ${pid}`);
```

```cjs
const { pid } = require('node:process');

console.log(`This process is pid ${pid}`);
```
