### Static method: `Buffer.allocUnsafe(size)`

<!-- YAML
added: v5.10.0
changes:
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/34682
    description: Throw ERR_INVALID_ARG_VALUE instead of ERR_INVALID_OPT_VALUE
                 for invalid input arguments.
  - version: v7.0.0
    pr-url: https://github.com/nodejs/node/pull/7079
    description: Passing a negative `size` will now throw an error.
-->

* `size` {integer} The desired length of the new `Buffer`.

Allocates a new `Buffer` of `size` bytes. If `size` is larger than
[`buffer.constants.MAX_LENGTH`][] or smaller than 0, [`ERR_INVALID_ARG_VALUE`][]
is thrown.

The underlying memory for `Buffer` instances created in this way is _not
initialized_. The contents of the newly created `Buffer` are unknown and
_may contain sensitive data_. Use [`Buffer.alloc()`][] instead to initialize
`Buffer` instances with zeroes.

```mjs
import { Buffer } from 'node:buffer';

const buf = Buffer.allocUnsafe(10);

console.log(buf);
// Prints (contents may vary): <Buffer a0 8b 28 3f 01 00 00 00 50 32>

buf.fill(0);

console.log(buf);
// Prints: <Buffer 00 00 00 00 00 00 00 00 00 00>
```

```cjs
const { Buffer } = require('node:buffer');

const buf = Buffer.allocUnsafe(10);

console.log(buf);
// Prints (contents may vary): <Buffer a0 8b 28 3f 01 00 00 00 50 32>

buf.fill(0);

console.log(buf);
// Prints: <Buffer 00 00 00 00 00 00 00 00 00 00>
```

A `TypeError` will be thrown if `size` is not a number.

The `Buffer` module pre-allocates an internal `Buffer` instance of
size [`Buffer.poolSize`][] that is used as a pool for the fast allocation of new
`Buffer` instances created using [`Buffer.allocUnsafe()`][],
[`Buffer.from(array)`][], [`Buffer.concat()`][], and the deprecated
`new Buffer(size)` constructor only when `size` is less than or equal
to `Buffer.poolSize >> 1` (floor of [`Buffer.poolSize`][] divided by two).

Use of this pre-allocated internal memory pool is a key difference between
calling `Buffer.alloc(size, fill)` vs. `Buffer.allocUnsafe(size).fill(fill)`.
Specifically, `Buffer.alloc(size, fill)` will _never_ use the internal `Buffer`
pool, while `Buffer.allocUnsafe(size).fill(fill)` _will_ use the internal
`Buffer` pool if `size` is less than or equal to half [`Buffer.poolSize`][]. The
difference is subtle but can be important when an application requires the
additional performance that [`Buffer.allocUnsafe()`][] provides.
