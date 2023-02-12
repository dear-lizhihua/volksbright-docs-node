## `util.transferableAbortController()`

<!-- YAML
added: v18.11.0
-->

> Stability: 1 - Experimental

Creates and returns an {AbortController} instance whose {AbortSignal} is marked
as transferable and can be used with `structuredClone()` or `postMessage()`.
