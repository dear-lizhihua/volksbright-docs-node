# Async hooks

<!--introduced_in=v8.1.0-->

> Stability: 1 - Experimental. Please migrate away from this API, if you can.
> We do not recommend using the [`createHook`][], [`AsyncHook`][], and
> [`executionAsyncResource`][] APIs as they have usability issues, safety risks,
> and performance implications. Async context tracking use cases are better
> served by the stable [`AsyncLocalStorage`][] API. If you have a use case for
> `createHook`, `AsyncHook`, or `executionAsyncResource` beyond the context
> tracking need solved by [`AsyncLocalStorage`][] or diagnostics data currently
> provided by [Diagnostics Channel][], please open an issue at
> <https://github.com/nodejs/node/issues> describing your use case so we can
> create a more purpose-focused API.

<!-- source_link=lib/async_hooks.js -->

We strongly discourage the use of the `async_hooks` API.
Other APIs that can cover most of its use cases include:

* [`AsyncLocalStorage`][] tracks async context
* [`process.getActiveResourcesInfo()`][] tracks active resources

The `node:async_hooks` module provides an API to track asynchronous resources.
It can be accessed using:

```mjs
import async_hooks from 'node:async_hooks';
```

```cjs
const async_hooks = require('node:async_hooks');
```
