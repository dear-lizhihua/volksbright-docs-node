# Web Crypto API

<!-- YAML
changes:
  - version: REPLACEME
    pr-url: https://github.com/nodejs/node/pull/46067
    description: Arguments are now coersed and validated as per their WebIDL
      definitions like in other Web Crypto API implementations.
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/44897
    description: No longer experimental except for the `Ed25519`, `Ed448`,
      `X25519`, and `X448` algorithms.
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/43310
    description: Removed proprietary `'node.keyObject'` import/export format.
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/43310
    description: Removed proprietary `'NODE-DSA'`, `'NODE-DH'`,
      and `'NODE-SCRYPT'` algorithms.
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42507
    description: Added `'Ed25519'`, `'Ed448'`, `'X25519'`, and `'X448'`
      algorithms.
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42507
    description: Removed proprietary `'NODE-ED25519'` and `'NODE-ED448'`
      algorithms.
  - version:
    - v18.4.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42507
    description: Removed proprietary `'NODE-X25519'` and `'NODE-X448'` named
      curves from the `'ECDH'` algorithm.
-->

<!-- introduced_in=v15.0.0 -->

> Stability: 2 - Stable

Node.js provides an implementation of the standard [Web Crypto API][].

Use `globalThis.crypto` or `require('node:crypto').webcrypto` to access this
module.

```js
const { subtle } = globalThis.crypto;

(async function() {

  const key = await subtle.generateKey({
    name: 'HMAC',
    hash: 'SHA-256',
    length: 256,
  }, true, ['sign', 'verify']);

  const enc = new TextEncoder();
  const message = enc.encode('I love cupcakes');

  const digest = await subtle.sign({
    name: 'HMAC',
  }, key, message);

})();
```
