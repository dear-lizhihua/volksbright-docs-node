### Event: `'close'`

<!-- YAML
added: v0.7.7
-->

* `code` {number} The exit code if the child exited on its own.
* `signal` {string} The signal by which the child process was terminated.

The `'close'` event is emitted after a process has ended _and_ the stdio
streams of a child process have been closed. This is distinct from the
[`'exit'`][] event, since multiple processes might share the same stdio
streams. The `'close'` event will always emit after [`'exit'`][] was
already emitted, or [`'error'`][] if the child failed to spawn.

```js
const { spawn } = require('node:child_process');
const ls = spawn('ls', ['-lh', '/usr']);

ls.stdout.on('data', (data) => {
  console.log(`stdout: ${data}`);
});

ls.on('close', (code) => {
  console.log(`child process close all stdio with code ${code}`);
});

ls.on('exit', (code) => {
  console.log(`child process exited with code ${code}`);
});
```
