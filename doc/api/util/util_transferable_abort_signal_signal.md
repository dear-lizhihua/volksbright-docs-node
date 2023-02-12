## `util.transferableAbortSignal(signal)`

<!-- YAML
added: v18.11.0
-->

> Stability: 1 - Experimental

* `signal` {AbortSignal}
* Returns: {AbortSignal}

Marks the given {AbortSignal} as transferable so that it can be used with
`structuredClone()` and `postMessage()`.

```js
const signal = transferableAbortSignal(AbortSignal.timeout(100));
const channel = new MessageChannel();
channel.port2.postMessage(signal, [signal]);
```
