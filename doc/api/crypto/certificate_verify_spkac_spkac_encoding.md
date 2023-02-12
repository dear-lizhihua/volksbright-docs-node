#### `certificate.verifySpkac(spkac[, encoding])`

<!-- YAML
added: v0.11.8
-->

* `spkac` {string|ArrayBuffer|Buffer|TypedArray|DataView}
* `encoding` {string} The [encoding][] of the `spkac` string.
* Returns: {boolean} `true` if the given `spkac` data structure is valid,
  `false` otherwise.

```mjs
import { Buffer } from 'node:buffer';
const { Certificate } = await import('node:crypto');

const cert = Certificate();
const spkac = getSpkacSomehow();
console.log(cert.verifySpkac(Buffer.from(spkac)));
// Prints: true or false
```

```cjs
const { Certificate } = require('node:crypto');
const { Buffer } = require('node:buffer');

const cert = Certificate();
const spkac = getSpkacSomehow();
console.log(cert.verifySpkac(Buffer.from(spkac)));
// Prints: true or false
```
