# File system

<!--introduced_in=v0.10.0-->

> Stability: 2 - Stable

<!--name=fs-->

<!-- source_link=lib/fs.js -->

The `node:fs` module enables interacting with the file system in a
way modeled on standard POSIX functions.

To use the promise-based APIs:

```mjs
import * as fs from 'node:fs/promises';
```

```cjs
const fs = require('node:fs/promises');
```

To use the callback and sync APIs:

```mjs
import * as fs from 'node:fs';
```

```cjs
const fs = require('node:fs');
```

All file system operations have synchronous, callback, and promise-based
forms, and are accessible using both CommonJS syntax and ES6 Modules (ESM).
