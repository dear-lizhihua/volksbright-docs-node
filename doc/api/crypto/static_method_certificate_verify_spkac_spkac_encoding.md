### Static method: `Certificate.verifySpkac(spkac[, encoding])`

<!-- YAML
added: v9.0.0
changes:
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/35093
    description: The spkac argument can be an ArrayBuffer. Added encoding.
                 Limited the size of the spkac argument to a maximum of
                 2**31 - 1 bytes.
-->

* `spkac` {string|ArrayBuffer|Buffer|TypedArray|DataView}
* `encoding` {string} The [encoding][] of the `spkac` string.
* Returns: {boolean} `true` if the given `spkac` data structure is valid,
  `false` otherwise.

```mjs
import { Buffer } from 'node:buffer';
const { Certificate } = await import('node:crypto');

const spkac = getSpkacSomehow();
console.log(Certificate.verifySpkac(Buffer.from(spkac)));
// Prints: true or false
```

```cjs
const { Certificate } = require('node:crypto');
const { Buffer } = require('node:buffer');

const spkac = getSpkacSomehow();
console.log(Certificate.verifySpkac(Buffer.from(spkac)));
// Prints: true or false
```
