## Promise hooks

The `promiseHooks` interface can be used to track promise lifecycle events.
To track _all_ async activity, see [`async_hooks`][] which internally uses this
module to produce promise lifecycle events in addition to events for other
async resources. For request context management, see [`AsyncLocalStorage`][].

```mjs
import { promiseHooks } from 'node:v8';

// There are four lifecycle events produced by promises:

// The `init` event represents the creation of a promise. This could be a
// direct creation such as with `new Promise(...)` or a continuation such
// as `then()` or `catch()`. It also happens whenever an async function is
// called or does an `await`. If a continuation promise is created, the
// `parent` will be the promise it is a continuation from.
function init(promise, parent) {
  console.log('a promise was created', { promise, parent });
}

// The `settled` event happens when a promise receives a resolution or
// rejection value. This may happen synchronously such as when using
// `Promise.resolve()` on non-promise input.
function settled(promise) {
  console.log('a promise resolved or rejected', { promise });
}

// The `before` event runs immediately before a `then()` or `catch()` handler
// runs or an `await` resumes execution.
function before(promise) {
  console.log('a promise is about to call a then handler', { promise });
}

// The `after` event runs immediately after a `then()` handler runs or when
// an `await` begins after resuming from another.
function after(promise) {
  console.log('a promise is done calling a then handler', { promise });
}

// Lifecycle hooks may be started and stopped individually
const stopWatchingInits = promiseHooks.onInit(init);
const stopWatchingSettleds = promiseHooks.onSettled(settled);
const stopWatchingBefores = promiseHooks.onBefore(before);
const stopWatchingAfters = promiseHooks.onAfter(after);

// Or they may be started and stopped in groups
const stopHookSet = promiseHooks.createHook({
  init,
  settled,
  before,
  after,
});

// To stop a hook, call the function returned at its creation.
stopWatchingInits();
stopWatchingSettleds();
stopWatchingBefores();
stopWatchingAfters();
stopHookSet();
```
