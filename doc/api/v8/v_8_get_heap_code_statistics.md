## `v8.getHeapCodeStatistics()`

<!-- YAML
added: v12.8.0
-->

* Returns: {Object}

Get statistics about code and its metadata in the heap, see V8
[`GetHeapCodeAndMetadataStatistics`][] API. Returns an object with the
following properties:

* `code_and_metadata_size` {number}
* `bytecode_and_metadata_size` {number}
* `external_script_source_size` {number}
* `cpu_profiler_metadata_size` {number}

<!-- eslint-skip -->

```js
{
  code_and_metadata_size: 212208,
  bytecode_and_metadata_size: 161368,
  external_script_source_size: 1410794,
  cpu_profiler_metadata_size: 0,
}
```
