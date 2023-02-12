## Class: `DiffieHellmanGroup`

<!-- YAML
added: v0.7.5
-->

The `DiffieHellmanGroup` class takes a well-known modp group as its argument.
It works the same as `DiffieHellman`, except that it does not allow changing
its keys after creation. In other words, it does not implement `setPublicKey()`
or `setPrivateKey()` methods.

```mjs
const { createDiffieHellmanGroup } = await import('node:crypto');
const dh = createDiffieHellmanGroup('modp16');
```

```cjs
const { createDiffieHellmanGroup } = require('node:crypto');
const dh = createDiffieHellmanGroup('modp16');
```

The following groups are supported:

* `'modp14'` (2048 bits, [RFC 3526][] Section 3)
* `'modp15'` (3072 bits, [RFC 3526][] Section 4)
* `'modp16'` (4096 bits, [RFC 3526][] Section 5)
* `'modp17'` (6144 bits, [RFC 3526][] Section 6)
* `'modp18'` (8192 bits, [RFC 3526][] Section 7)

The following groups are still supported but deprecated (see [Caveats][]):

* `'modp1'` (768 bits, [RFC 2409][] Section 6.1) <span class="deprecated-inline"></span>
* `'modp2'` (1024 bits, [RFC 2409][] Section 6.2) <span class="deprecated-inline"></span>
* `'modp5'` (1536 bits, [RFC 3526][] Section 2) <span class="deprecated-inline"></span>

These deprecated groups might be removed in future versions of Node.js.
