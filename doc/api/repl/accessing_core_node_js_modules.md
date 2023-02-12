#### Accessing core Node.js modules

The default evaluator will automatically load Node.js core modules into the
REPL environment when used. For instance, unless otherwise declared as a
global or scoped variable, the input `fs` will be evaluated on-demand as
`global.fs = require('node:fs')`.

```console
> fs.createReadStream('./some/file');
```
