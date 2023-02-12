## `v8.getHeapStatistics()`

<!-- YAML
added: v1.0.0
changes:
  - version: v7.5.0
    pr-url: https://github.com/nodejs/node/pull/10186
    description: Support values exceeding the 32-bit unsigned integer range.
  - version: v7.2.0
    pr-url: https://github.com/nodejs/node/pull/8610
    description: Added `malloced_memory`, `peak_malloced_memory`,
                 and `does_zap_garbage`.
-->

* Returns: {Object}

Returns an object with the following properties:

* `total_heap_size` {number}
* `total_heap_size_executable` {number}
* `total_physical_size` {number}
* `total_available_size` {number}
* `used_heap_size` {number}
* `heap_size_limit` {number}
* `malloced_memory` {number}
* `peak_malloced_memory` {number}
* `does_zap_garbage` {number}
* `number_of_native_contexts` {number}
* `number_of_detached_contexts` {number}
* `total_global_handles_size` {number}
* `used_global_handles_size` {number}
* `external_memory` {number}

`does_zap_garbage` is a 0/1 boolean, which signifies whether the
`--zap_code_space` option is enabled or not. This makes V8 overwrite heap
garbage with a bit pattern. The RSS footprint (resident set size) gets bigger
because it continuously touches all heap pages and that makes them less likely
to get swapped out by the operating system.

`number_of_native_contexts` The value of native\_context is the number of the
top-level contexts currently active. Increase of this number over time indicates
a memory leak.

`number_of_detached_contexts` The value of detached\_context is the number
of contexts that were detached and not yet garbage collected. This number
being non-zero indicates a potential memory leak.

`total_global_handles_size` The value of total\_global\_handles\_size is the
total memory size of V8 global handles.

`used_global_handles_size` The value of used\_global\_handles\_size is the
used memory size of V8 global handles.

`external_memory` The value of external\_memory is the memory size of array
buffers and external strings.

<!-- eslint-skip -->

```js
{
  total_heap_size: 7326976,
  total_heap_size_executable: 4194304,
  total_physical_size: 7326976,
  total_available_size: 1152656,
  used_heap_size: 3476208,
  heap_size_limit: 1535115264,
  malloced_memory: 16384,
  peak_malloced_memory: 1127496,
  does_zap_garbage: 0,
  number_of_native_contexts: 1,
  number_of_detached_contexts: 0,
  total_global_handles_size: 8192,
  used_global_handles_size: 3296,
  external_memory: 318824
}
```
