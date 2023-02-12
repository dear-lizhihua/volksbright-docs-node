## Introduction

These classes are used to associate state and propagate it throughout
callbacks and promise chains.
They allow storing data throughout the lifetime of a web request
or any other asynchronous duration. It is similar to thread-local storage
in other languages.

The `AsyncLocalStorage` and `AsyncResource` classes are part of the
`node:async_hooks` module:

```mjs
import { AsyncLocalStorage, AsyncResource } from 'node:async_hooks';
```

```cjs
const { AsyncLocalStorage, AsyncResource } = require('node:async_hooks');
```
