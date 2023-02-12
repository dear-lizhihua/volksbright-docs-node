#### `new crypto.Certificate()`

Instances of the `Certificate` class can be created using the `new` keyword
or by calling `crypto.Certificate()` as a function:

```mjs
const { Certificate } = await import('node:crypto');

const cert1 = new Certificate();
const cert2 = Certificate();
```

```cjs
const { Certificate } = require('node:crypto');

const cert1 = new Certificate();
const cert2 = Certificate();
```
