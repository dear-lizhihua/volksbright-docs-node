## Import assertions

<!-- YAML
added:
  - v17.1.0
  - v16.14.0
-->

> Stability: 1 - Experimental

The [Import Assertions proposal][] adds an inline syntax for module import
statements to pass on more information alongside the module specifier.

```js
import fooData from './foo.json' assert { type: 'json' };

const { default: barData } =
  await import('./bar.json', { assert: { type: 'json' } });
```

Node.js supports the following `type` values, for which the assertion is
mandatory:

| Assertion `type` | Needed for       |
| ---------------- | ---------------- |
| `'json'`         | [JSON modules][] |
