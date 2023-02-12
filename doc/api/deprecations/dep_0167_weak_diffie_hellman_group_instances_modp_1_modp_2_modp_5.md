### DEP0167: Weak `DiffieHellmanGroup` instances (`modp1`, `modp2`, `modp5`)

<!-- YAML
changes:
  - version:
    - v18.10.0
    - v16.18.0
    pr-url: https://github.com/nodejs/node/pull/44588
    description: Documentation-only deprecation.
-->

Type: Documentation-only

The well-known MODP groups `modp1`, `modp2`, and `modp5` are deprecated because
they are not secure against practical attacks. See [RFC 8247 Section 2.4][] for
details.

These groups might be removed in future versions of Node.js. Applications that
rely on these groups should evaluate using stronger MODP groups instead.
