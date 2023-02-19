### `context.signal`

<!-- YAML
added:
  - v18.7.0
  - v16.17.0
-->

* {AbortSignal} Can be used to abort test subtasks when the test has been
  aborted.

```js
test('top level test', async (t) => {
  await fetch('some/uri', { signal: t.signal });
});
```
