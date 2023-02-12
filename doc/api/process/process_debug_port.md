## `process.debugPort`

<!-- YAML
added: v0.7.2
-->

* {number}

The port used by the Node.js debugger when enabled.

```mjs
import process from 'node:process';

process.debugPort = 5858;
```

```cjs
const process = require('node:process');

process.debugPort = 5858;
```
