### Spawning `.bat` and `.cmd` files on Windows

The importance of the distinction between [`child_process.exec()`][] and
[`child_process.execFile()`][] can vary based on platform. On Unix-type
operating systems (Unix, Linux, macOS) [`child_process.execFile()`][] can be
more efficient because it does not spawn a shell by default. On Windows,
however, `.bat` and `.cmd` files are not executable on their own without a
terminal, and therefore cannot be launched using [`child_process.execFile()`][].
When running on Windows, `.bat` and `.cmd` files can be invoked using
[`child_process.spawn()`][] with the `shell` option set, with
[`child_process.exec()`][], or by spawning `cmd.exe` and passing the `.bat` or
`.cmd` file as an argument (which is what the `shell` option and
[`child_process.exec()`][] do). In any case, if the script filename contains
spaces it needs to be quoted.

```js
// On Windows Only...
const { spawn } = require('node:child_process');
const bat = spawn('cmd.exe', ['/c', 'my.bat']);

bat.stdout.on('data', (data) => {
  console.log(data.toString());
});

bat.stderr.on('data', (data) => {
  console.error(data.toString());
});

bat.on('exit', (code) => {
  console.log(`Child exited with code ${code}`);
});
```

```js
// OR...
const { exec, spawn } = require('node:child_process');
exec('my.bat', (err, stdout, stderr) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(stdout);
});

// Script with spaces in the filename:
const bat = spawn('"my script.cmd"', ['a', 'b'], { shell: true });
// or:
exec('"my script.cmd" a b', (err, stdout, stderr) => {
  // ...
});
```
