##### `writable.destroyed`

<!-- YAML
added: v8.0.0
-->

* {boolean}

Is `true` after [`writable.destroy()`][writable-destroy] has been called.

```cjs
const { Writable } = require('node:stream');

const myStream = new Writable();

console.log(myStream.destroyed); // false
myStream.destroy();
console.log(myStream.destroyed); // true
```
