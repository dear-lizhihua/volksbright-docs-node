### `--abort-on-uncaught-exception`

<!-- YAML
added: v0.10.8
-->

Aborting instead of exiting causes a core file to be generated for post-mortem
analysis using a debugger (such as `lldb`, `gdb`, and `mdb`).

If this flag is passed, the behavior can still be set to not abort through
[`process.setUncaughtExceptionCaptureCallback()`][] (and through usage of the
`node:domain` module that uses it).
