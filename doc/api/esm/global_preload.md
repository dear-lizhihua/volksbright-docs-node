#### `globalPreload()`

<!-- YAML
changes:
  - version:
    - v18.6.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42623
    description: Add support for chaining globalPreload hooks.
-->

> The loaders API is being redesigned. This hook may disappear or its
> signature may change. Do not rely on the API described below.

> In a previous version of this API, this hook was named
> `getGlobalPreloadCode`.

* `context` {Object} Information to assist the preload code
  * `port` {MessagePort}
* Returns: {string} Code to run before application startup

Sometimes it might be necessary to run some code inside of the same global
scope that the application runs in. This hook allows the return of a string
that is run as a sloppy-mode script on startup.

Similar to how CommonJS wrappers work, the code runs in an implicit function
scope. The only argument is a `require`-like function that can be used to load
builtins like "fs": `getBuiltin(request: string)`.

If the code needs more advanced `require` features, it has to construct
its own `require` using  `module.createRequire()`.

```js
export function globalPreload(context) {
  return `\
globalThis.someInjectedProperty = 42;
console.log('I just set some globals!');

const { createRequire } = getBuiltin('module');
const { cwd } = getBuiltin('process');

const require = createRequire(cwd() + '/<preload>');
// [...]
`;
}
```

In order to allow communication between the application and the loader, another
argument is provided to the preload code: `port`. This is available as a
parameter to the loader hook and inside of the source text returned by the hook.
Some care must be taken in order to properly call [`port.ref()`][] and
[`port.unref()`][] to prevent a process from being in a state where it won't
close normally.

```js
/**
 * This example has the application context send a message to the loader
 * and sends the message back to the application context
 */
export function globalPreload({ port }) {
  port.onmessage = (evt) => {
    port.postMessage(evt.data);
  };
  return `\
    port.postMessage('console.log("I went to the Loader and back");');
    port.onmessage = (evt) => {
      eval(evt.data);
    };
  `;
}
```
