### `process.report.directory`

<!-- YAML
added: v11.12.0
changes:
  - version:
     - v13.12.0
     - v12.17.0
    pr-url: https://github.com/nodejs/node/pull/32242
    description: This API is no longer experimental.
-->

* {string}

Directory where the report is written. The default value is the empty string,
indicating that reports are written to the current working directory of the
Node.js process.

```mjs
import { report } from 'node:process';

console.log(`Report directory is ${report.directory}`);
```

```cjs
const { report } = require('node:process');

console.log(`Report directory is ${report.directory}`);
```
