#### `event.returnValue`

<!-- YAML
added: v14.5.0
-->

> Stability: 3 - Legacy: Use [`event.defaultPrevented`][] instead.

* Type: {boolean} True if the event has not been canceled.

The value of `event.returnValue` is always the opposite of `event.defaultPrevented`.
This is not used in Node.js and is provided purely for completeness.
