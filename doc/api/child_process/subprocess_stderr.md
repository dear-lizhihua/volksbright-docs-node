### `subprocess.stderr`

<!-- YAML
added: v0.1.90
-->

* {stream.Readable|null|undefined}

A `Readable Stream` that represents the child process's `stderr`.

If the child was spawned with `stdio[2]` set to anything other than `'pipe'`,
then this will be `null`.

`subprocess.stderr` is an alias for `subprocess.stdio[2]`. Both properties will
refer to the same value.

The `subprocess.stderr` property can be `null` or `undefined`
if the child process could not be successfully spawned.
