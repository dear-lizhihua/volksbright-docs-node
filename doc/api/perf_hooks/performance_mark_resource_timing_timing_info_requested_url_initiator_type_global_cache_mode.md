### `performance.markResourceTiming(timingInfo, requestedUrl, initiatorType, global, cacheMode)`

<!-- YAML
added:
  - v18.2.0
  - v16.17.0
-->

* `timingInfo` {Object} [Fetch Timing Info][]
* `requestedUrl` {string} The resource url
* `initiatorType` {string} The initiator name, e.g: 'fetch'
* `global` {Object}
* `cacheMode` {string} The cache mode must be an empty string ('') or 'local'

_This property is an extension by Node.js. It is not available in Web browsers._

Creates a new `PerformanceResourceTiming` entry in the Resource Timeline. A
`PerformanceResourceTiming` is a subclass of `PerformanceEntry` whose
`performanceEntry.entryType` is always `'resource'`. Performance resources
are used to mark moments in the Resource Timeline.

The created `PerformanceMark` entry is put in the global Resource Timeline
and can be queried with `performance.getEntries`,
`performance.getEntriesByName`, and `performance.getEntriesByType`. When the
observation is performed, the entries should be cleared from the global
Performance Timeline manually with `performance.clearResourceTimings`.
