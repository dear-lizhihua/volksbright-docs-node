## `process.version`

<!-- YAML
added: v0.1.3
-->

* {string}

The `process.version` property contains the Node.js version string.

```mjs
import { version } from 'node:process';

console.log(`Version: ${version}`);
// Version: v14.8.0
```

```cjs
const { version } = require('node:process');

console.log(`Version: ${version}`);
// Version: v14.8.0
```

To get the version string without the prepended _v_, use
`process.versions.node`.
