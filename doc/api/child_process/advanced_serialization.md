## Advanced serialization

<!-- YAML
added:
 - v13.2.0
 - v12.16.0
-->

Child processes support a serialization mechanism for IPC that is based on the
[serialization API of the `node:v8` module][v8.serdes], based on the
[HTML structured clone algorithm][]. This is generally more powerful and
supports more built-in JavaScript object types, such as `BigInt`, `Map`
and `Set`, `ArrayBuffer` and `TypedArray`, `Buffer`, `Error`, `RegExp` etc.

However, this format is not a full superset of JSON, and e.g. properties set on
objects of such built-in types will not be passed on through the serialization
step. Additionally, performance may not be equivalent to that of JSON, depending
on the structure of the passed data.
Therefore, this feature requires opting in by setting the
`serialization` option to `'advanced'` when calling [`child_process.spawn()`][]
or [`child_process.fork()`][].

[Advanced serialization]: #advanced-serialization
[Default Windows shell]: #default-windows-shell
[HTML structured clone algorithm]: https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm
[Shell requirements]: #shell-requirements
[Signal Events]: process.md#signal-events
[`'disconnect'`]: process.md#event-disconnect
[`'error'`]: #event-error
[`'exit'`]: #event-exit
[`'message'`]: process.md#event-message
[`ChildProcess`]: #class-childprocess
[`Error`]: errors.md#class-error
[`EventEmitter`]: events.md#class-eventemitter
[`child_process.exec()`]: #child_processexeccommand-options-callback
[`child_process.execFile()`]: #child_processexecfilefile-args-options-callback
[`child_process.execFileSync()`]: #child_processexecfilesyncfile-args-options
[`child_process.execSync()`]: #child_processexecsynccommand-options
[`child_process.fork()`]: #child_processforkmodulepath-args-options
[`child_process.spawn()`]: #child_processspawncommand-args-options
[`child_process.spawnSync()`]: #child_processspawnsynccommand-args-options
[`maxBuffer` and Unicode]: #maxbuffer-and-unicode
[`net.Server`]: net.md#class-netserver
[`net.Socket`]: net.md#class-netsocket
[`options.detached`]: #optionsdetached
[`process.disconnect()`]: process.md#processdisconnect
[`process.env`]: process.md#processenv
[`process.execPath`]: process.md#processexecpath
[`process.send()`]: process.md#processsendmessage-sendhandle-options-callback
[`stdio`]: #optionsstdio
[`subprocess.connected`]: #subprocessconnected
[`subprocess.disconnect()`]: #subprocessdisconnect
[`subprocess.kill()`]: #subprocesskillsignal
[`subprocess.send()`]: #subprocesssendmessage-sendhandle-options-callback
[`subprocess.stderr`]: #subprocessstderr
[`subprocess.stdin`]: #subprocessstdin
[`subprocess.stdio`]: #subprocessstdio
[`subprocess.stdout`]: #subprocessstdout
[`util.promisify()`]: util.md#utilpromisifyoriginal
[synchronous counterparts]: #synchronous-process-creation
[v8.serdes]: v8.md#serialization-api
