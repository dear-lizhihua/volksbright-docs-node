## `process.argv`

<!-- YAML
added: v0.1.27
-->

* {string\[]}

The `process.argv` property returns an array containing the command-line
arguments passed when the Node.js process was launched. The first element will
be [`process.execPath`][]. See `process.argv0` if access to the original value
of `argv[0]` is needed. The second element will be the path to the JavaScript
file being executed. The remaining elements will be any additional command-line
arguments.

For example, assuming the following script for `process-args.js`:

```mjs
import { argv } from 'node:process';

// print process.argv
argv.forEach((val, index) => {
  console.log(`${index}: ${val}`);
});
```

```cjs
const { argv } = require('node:process');

// print process.argv
argv.forEach((val, index) => {
  console.log(`${index}: ${val}`);
});
```

Launching the Node.js process as:

```console
$ node process-args.js one two=three four
```

Would generate the output:

```text
0: /usr/local/bin/node
1: /Users/mjr/work/node/process-args.js
2: one
3: two=three
4: four
```
