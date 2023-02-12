#### `buffer.constants.MAX_LENGTH`

<!-- YAML
added: v8.2.0
changes:
  - version: v15.0.0
    pr-url: https://github.com/nodejs/node/pull/35415
    description: Value is changed to 2<sup>32</sup> on 64-bit
      architectures.
  - version: v14.0.0
    pr-url: https://github.com/nodejs/node/pull/32116
    description: Value is changed from 2<sup>31</sup> - 1 to
      2<sup>32</sup> - 1 on 64-bit architectures.
-->

* {integer} The largest size allowed for a single `Buffer` instance.

On 32-bit architectures, this value currently is 2<sup>30</sup> - 1 (about 1
GiB).

On 64-bit architectures, this value currently is 2<sup>32</sup> (about 4 GiB).

It reflects [`v8::TypedArray::kMaxLength`][] under the hood.

This value is also available as [`buffer.kMaxLength`][].
