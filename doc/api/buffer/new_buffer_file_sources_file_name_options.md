### `new buffer.File(sources, fileName[, options])`

<!-- YAML
added:
  - v19.2.0
  - v18.13.0
-->

* `sources` {string\[]|ArrayBuffer\[]|TypedArray\[]|DataView\[]|Blob\[]|File\[]}
  An array of string, {ArrayBuffer}, {TypedArray}, {DataView}, {File}, or {Blob}
  objects, or any mix of such objects, that will be stored within the `File`.
* `fileName` {string} The name of the file.
* `options` {Object}
  * `endings` {string} One of either `'transparent'` or `'native'`. When set
    to `'native'`, line endings in string source parts will be converted to
    the platform native line-ending as specified by `require('node:os').EOL`.
  * `type` {string} The File content-type.
  * `lastModified` {number} The last modified date of the file.
    **Default:** `Date.now()`.
