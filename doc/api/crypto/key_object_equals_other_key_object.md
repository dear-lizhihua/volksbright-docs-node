### `keyObject.equals(otherKeyObject)`

<!-- YAML
added:
  - v17.7.0
  - v16.15.0
-->

* `otherKeyObject`: {KeyObject} A `KeyObject` with which to
  compare `keyObject`.
* Returns: {boolean}

Returns `true` or `false` depending on whether the keys have exactly the same
type, value, and parameters. This method is not
[constant time](https://en.wikipedia.org/wiki/Timing_attack).
