### `profiler.stop()`

<!-- YAML
added: v19.6.0
-->

Stop collecting GC data and return an object.The content of object
is as follows.

```json
{
  "version": 1,
  "startTime": 1674059033862,
  "statistics": [
    {
      "gcType": "Scavenge",
      "beforeGC": {
        "heapStatistics": {
          "totalHeapSize": 5005312,
          "totalHeapSizeExecutable": 524288,
          "totalPhysicalSize": 5226496,
          "totalAvailableSize": 4341325216,
          "totalGlobalHandlesSize": 8192,
          "usedGlobalHandlesSize": 2112,
          "usedHeapSize": 4883840,
          "heapSizeLimit": 4345298944,
          "mallocedMemory": 254128,
          "externalMemory": 225138,
          "peakMallocedMemory": 181760
        },
        "heapSpaceStatistics": [
          {
            "spaceName": "read_only_space",
            "spaceSize": 0,
            "spaceUsedSize": 0,
            "spaceAvailableSize": 0,
            "physicalSpaceSize": 0
          }
        ]
      },
      "cost": 1574.14,
      "afterGC": {
        "heapStatistics": {
          "totalHeapSize": 6053888,
          "totalHeapSizeExecutable": 524288,
          "totalPhysicalSize": 5500928,
          "totalAvailableSize": 4341101384,
          "totalGlobalHandlesSize": 8192,
          "usedGlobalHandlesSize": 2112,
          "usedHeapSize": 4059096,
          "heapSizeLimit": 4345298944,
          "mallocedMemory": 254128,
          "externalMemory": 225138,
          "peakMallocedMemory": 181760
        },
        "heapSpaceStatistics": [
          {
            "spaceName": "read_only_space",
            "spaceSize": 0,
            "spaceUsedSize": 0,
            "spaceAvailableSize": 0,
            "physicalSpaceSize": 0
          }
        ]
      }
    }
  ],
  "endTime": 1674059036865
}
```

Here's an example.

```js
const { GCProfiler } = require('v8');
const profiler = new GCProfiler();
profiler.start();
setTimeout(() => {
  console.log(profiler.stop());
}, 1000);
```

[HTML structured clone algorithm]: https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm
[Hook Callbacks]: #hook-callbacks
[V8]: https://developers.google.com/v8/
[`--heapsnapshot-near-heap-limit`]: cli.md#--heapsnapshot-near-heap-limitmax_count
[`AsyncLocalStorage`]: async_context.md#class-asynclocalstorage
[`Buffer`]: buffer.md
[`DefaultDeserializer`]: #class-v8defaultdeserializer
[`DefaultSerializer`]: #class-v8defaultserializer
[`Deserializer`]: #class-v8deserializer
[`ERR_BUFFER_TOO_LARGE`]: errors.md#err_buffer_too_large
[`Error`]: errors.md#class-error
[`GetHeapCodeAndMetadataStatistics`]: https://v8docs.nodesource.com/node-13.2/d5/dda/classv8_1_1_isolate.html#a6079122af17612ef54ef3348ce170866
[`GetHeapSpaceStatistics`]: https://v8docs.nodesource.com/node-13.2/d5/dda/classv8_1_1_isolate.html#ac673576f24fdc7a33378f8f57e1d13a4
[`NODE_V8_COVERAGE`]: cli.md#node_v8_coveragedir
[`Serializer`]: #class-v8serializer
[`after` callback]: #afterpromise
[`async_hooks`]: async_hooks.md
[`before` callback]: #beforepromise
[`buffer.constants.MAX_LENGTH`]: buffer.md#bufferconstantsmax_length
[`deserializer._readHostObject()`]: #deserializer_readhostobject
[`deserializer.transferArrayBuffer()`]: #deserializertransferarraybufferid-arraybuffer
[`init` callback]: #initpromise-parent
[`serialize()`]: #v8serializevalue
[`serializer._getSharedArrayBufferId()`]: #serializer_getsharedarraybufferidsharedarraybuffer
[`serializer._writeHostObject()`]: #serializer_writehostobjectobject
[`serializer.releaseBuffer()`]: #serializerreleasebuffer
[`serializer.transferArrayBuffer()`]: #serializertransferarraybufferid-arraybuffer
[`serializer.writeRawBytes()`]: #serializerwriterawbytesbuffer
[`settled` callback]: #settledpromise
[`v8.stopCoverage()`]: #v8stopcoverage
[`v8.takeCoverage()`]: #v8takecoverage
[`vm.Script`]: vm.md#new-vmscriptcode-options
[worker threads]: worker_threads.md
