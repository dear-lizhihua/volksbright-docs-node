### Exports sugar

<!-- YAML
added: v12.11.0
-->

If the `"."` export is the only export, the [`"exports"`][] field provides sugar
for this case being the direct [`"exports"`][] field value.

```json
{
  "exports": {
    ".": "./index.js"
  }
}
```

can be written:

```json
{
  "exports": "./index.js"
}
```
