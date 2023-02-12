## Class: `X509Certificate`

<!-- YAML
added: v15.6.0
-->

Encapsulates an X509 certificate and provides read-only access to
its information.

```mjs
const { X509Certificate } = await import('node:crypto');

const x509 = new X509Certificate('{... pem encoded cert ...}');

console.log(x509.subject);
```

```cjs
const { X509Certificate } = require('node:crypto');

const x509 = new X509Certificate('{... pem encoded cert ...}');

console.log(x509.subject);
```
