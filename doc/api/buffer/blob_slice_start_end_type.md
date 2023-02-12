### `blob.slice([start[, end[, type]]])`

<!-- YAML
added:
  - v15.7.0
  - v14.18.0
-->

* `start` {number} The starting index.
* `end` {number} The ending index.
* `type` {string} The content-type for the new `Blob`

Creates and returns a new `Blob` containing a subset of this `Blob` objects
data. The original `Blob` is not altered.
