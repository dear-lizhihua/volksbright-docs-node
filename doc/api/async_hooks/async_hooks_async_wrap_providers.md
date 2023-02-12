### `async_hooks.asyncWrapProviders`

<!-- YAML
added:
  - v17.2.0
  - v16.14.0
-->

* Returns: A map of provider types to the corresponding numeric id.
  This map contains all the event types that might be emitted by the `async_hooks.init()` event.

This feature suppresses the deprecated usage of `process.binding('async_wrap').Providers`.
See: [DEP0111][]
