#### `options.stdio`

<!-- YAML
added: v0.7.10
changes:
  - version:
      - v15.6.0
      - v14.18.0
    pr-url: https://github.com/nodejs/node/pull/29412
    description: Added the `overlapped` stdio flag.
  - version: v3.3.1
    pr-url: https://github.com/nodejs/node/pull/2727
    description: The value `0` is now accepted as a file descriptor.
-->

The `options.stdio` option is used to configure the pipes that are established
between the parent and child process. By default, the child's stdin, stdout,
and stderr are redirected to corresponding [`subprocess.stdin`][],
[`subprocess.stdout`][], and [`subprocess.stderr`][] streams on the
[`ChildProcess`][] object. This is equivalent to setting the `options.stdio`
equal to `['pipe', 'pipe', 'pipe']`.

For convenience, `options.stdio` may be one of the following strings:

* `'pipe'`: equivalent to `['pipe', 'pipe', 'pipe']` (the default)
* `'overlapped'`: equivalent to `['overlapped', 'overlapped', 'overlapped']`
* `'ignore'`: equivalent to `['ignore', 'ignore', 'ignore']`
* `'inherit'`: equivalent to `['inherit', 'inherit', 'inherit']` or `[0, 1, 2]`

Otherwise, the value of `options.stdio` is an array where each index corresponds
to an fd in the child. The fds 0, 1, and 2 correspond to stdin, stdout,
and stderr, respectively. Additional fds can be specified to create additional
pipes between the parent and child. The value is one of the following:

1. `'pipe'`: Create a pipe between the child process and the parent process.
   The parent end of the pipe is exposed to the parent as a property on the
   `child_process` object as [`subprocess.stdio[fd]`][`subprocess.stdio`]. Pipes
   created for fds 0, 1, and 2 are also available as [`subprocess.stdin`][],
   [`subprocess.stdout`][] and [`subprocess.stderr`][], respectively.
   These are not actual Unix pipes and therefore the child process
   can not use them by their descriptor files,
   e.g. `/dev/fd/2` or `/dev/stdout`.
2. `'overlapped'`: Same as `'pipe'` except that the `FILE_FLAG_OVERLAPPED` flag
   is set on the handle. This is necessary for overlapped I/O on the child
   process's stdio handles. See the
   [docs](https://docs.microsoft.com/en-us/windows/win32/fileio/synchronous-and-asynchronous-i-o)
   for more details. This is exactly the same as `'pipe'` on non-Windows
   systems.
3. `'ipc'`: Create an IPC channel for passing messages/file descriptors
   between parent and child. A [`ChildProcess`][] may have at most one IPC
   stdio file descriptor. Setting this option enables the
   [`subprocess.send()`][] method. If the child is a Node.js process, the
   presence of an IPC channel will enable [`process.send()`][] and
   [`process.disconnect()`][] methods, as well as [`'disconnect'`][] and
   [`'message'`][] events within the child.

   Accessing the IPC channel fd in any way other than [`process.send()`][]
   or using the IPC channel with a child process that is not a Node.js instance
   is not supported.
4. `'ignore'`: Instructs Node.js to ignore the fd in the child. While Node.js
   will always open fds 0, 1, and 2 for the processes it spawns, setting the fd
   to `'ignore'` will cause Node.js to open `/dev/null` and attach it to the
   child's fd.
5. `'inherit'`: Pass through the corresponding stdio stream to/from the
   parent process. In the first three positions, this is equivalent to
   `process.stdin`, `process.stdout`, and `process.stderr`, respectively. In
   any other position, equivalent to `'ignore'`.
6. {Stream} object: Share a readable or writable stream that refers to a tty,
   file, socket, or a pipe with the child process. The stream's underlying
   file descriptor is duplicated in the child process to the fd that
   corresponds to the index in the `stdio` array. The stream must have an
   underlying descriptor (file streams do not until the `'open'` event has
   occurred).
7. Positive integer: The integer value is interpreted as a file descriptor
   that is open in the parent process. It is shared with the child
   process, similar to how {Stream} objects can be shared. Passing sockets
   is not supported on Windows.
8. `null`, `undefined`: Use default value. For stdio fds 0, 1, and 2 (in other
   words, stdin, stdout, and stderr) a pipe is created. For fd 3 and up, the
   default is `'ignore'`.

```js
const { spawn } = require('node:child_process');

// Child will use parent's stdios.
spawn('prg', [], { stdio: 'inherit' });

// Spawn child sharing only stderr.
spawn('prg', [], { stdio: ['pipe', 'pipe', process.stderr] });

// Open an extra fd=4, to interact with programs presenting a
// startd-style interface.
spawn('prg', [], { stdio: ['pipe', null, null, null, 'pipe'] });
```

_It is worth noting that when an IPC channel is established between the
parent and child processes, and the child is a Node.js process, the child
is launched with the IPC channel unreferenced (using `unref()`) until the
child registers an event handler for the [`'disconnect'`][] event
or the [`'message'`][] event. This allows the child to exit
normally without the process being held open by the open IPC channel._

On Unix-like operating systems, the [`child_process.spawn()`][] method
performs memory operations synchronously before decoupling the event loop
from the child. Applications with a large memory footprint may find frequent
[`child_process.spawn()`][] calls to be a bottleneck. For more information,
see [V8 issue 7381](https://bugs.chromium.org/p/v8/issues/detail?id=7381).

See also: [`child_process.exec()`][] and [`child_process.fork()`][].
