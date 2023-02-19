## Class: `zlib.ZlibBase`

<!-- YAML
added: v0.5.8
changes:
  - version:
     - v11.7.0
     - v10.16.0
    pr-url: https://github.com/nodejs/node/pull/24939
    description: This class was renamed from `Zlib` to `ZlibBase`.
-->

Not exported by the `node:zlib` module. It is documented here because it is the
base class of the compressor/decompressor classes.

This class inherits from [`stream.Transform`][], allowing `node:zlib` objects to
be used in pipes and similar stream operations.
