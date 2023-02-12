## `events.setMaxListeners(n[, ...eventTargets])`

<!-- YAML
added: v15.4.0
-->

* `n` {number} A non-negative number. The maximum number of listeners per
  `EventTarget` event.
* `...eventsTargets` {EventTarget\[]|EventEmitter\[]} Zero or more {EventTarget}
  or {EventEmitter} instances. If none are specified, `n` is set as the default
  max for all newly created {EventTarget} and {EventEmitter} objects.

```mjs
import { setMaxListeners, EventEmitter } from 'node:events';

const target = new EventTarget();
const emitter = new EventEmitter();

setMaxListeners(5, target, emitter);
```

```cjs
const {
  setMaxListeners,
  EventEmitter,
} = require('node:events');

const target = new EventTarget();
const emitter = new EventEmitter();

setMaxListeners(5, target, emitter);
```
