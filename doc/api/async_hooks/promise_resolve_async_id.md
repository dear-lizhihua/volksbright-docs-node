#### `promiseResolve(asyncId)`

<!-- YAML
added: v8.6.0
-->

* `asyncId` {number}

Called when the `resolve` function passed to the `Promise` constructor is
invoked (either directly or through other means of resolving a promise).

`resolve()` does not do any observable synchronous work.

The `Promise` is not necessarily fulfilled or rejected at this point if the
`Promise` was resolved by assuming the state of another `Promise`.

```js
new Promise((resolve) => resolve(true)).then((a) => {});
```

calls the following callbacks:

```text
init for PROMISE with id 5, trigger id: 1
  promise resolve 5      # corresponds to resolve(true)
init for PROMISE with id 6, trigger id: 5  # the Promise returned by then()
  before 6               # the then() callback is entered
  promise resolve 6      # the then() callback resolves the promise by returning
  after 6
```
