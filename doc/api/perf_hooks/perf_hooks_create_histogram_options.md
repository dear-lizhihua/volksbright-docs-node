## `perf_hooks.createHistogram([options])`

<!-- YAML
added:
  - v15.9.0
  - v14.18.0
-->

* `options` {Object}
  * `lowest` {number|bigint} The lowest discernible value. Must be an integer
    value greater than 0. **Default:** `1`.
  * `highest` {number|bigint} The highest recordable value. Must be an integer
    value that is equal to or greater than two times `lowest`.
    **Default:** `Number.MAX_SAFE_INTEGER`.
  * `figures` {number} The number of accuracy digits. Must be a number between
    `1` and `5`. **Default:** `3`.
* Returns {RecordableHistogram}

Returns a {RecordableHistogram}.
