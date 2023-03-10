## Example: Running an HTTP server within a VM

When using either [`script.runInThisContext()`][] or
[`vm.runInThisContext()`][], the code is executed within the current V8 global
context. The code passed to this VM context will have its own isolated scope.

In order to run a simple web server using the `node:http` module the code passed
to the context must either call `require('node:http')` on its own, or have a
reference to the `node:http` module passed to it. For instance:

```js
'use strict';
const vm = require('node:vm');

const code = `
((require) => {
  const http = require('node:http');

  http.createServer((request, response) => {
    response.writeHead(200, { 'Content-Type': 'text/plain' });
    response.end('Hello World\\n');
  }).listen(8124);

  console.log('Server running at http://127.0.0.1:8124/');
})`;

vm.runInThisContext(code)(require);
```

The `require()` in the above case shares the state with the context it is
passed from. This may introduce risks when untrusted code is executed, e.g.
altering objects in the context in unwanted ways.
