### File system flags

The following flags are available wherever the `flag` option takes a
string.

* `'a'`: Open file for appending.
  The file is created if it does not exist.

* `'ax'`: Like `'a'` but fails if the path exists.

* `'a+'`: Open file for reading and appending.
  The file is created if it does not exist.

* `'ax+'`: Like `'a+'` but fails if the path exists.

* `'as'`: Open file for appending in synchronous mode.
  The file is created if it does not exist.

* `'as+'`: Open file for reading and appending in synchronous mode.
  The file is created if it does not exist.

* `'r'`: Open file for reading.
  An exception occurs if the file does not exist.

* `'r+'`: Open file for reading and writing.
  An exception occurs if the file does not exist.

* `'rs+'`: Open file for reading and writing in synchronous mode. Instructs
  the operating system to bypass the local file system cache.

  This is primarily useful for opening files on NFS mounts as it allows
  skipping the potentially stale local cache. It has a very real impact on
  I/O performance so using this flag is not recommended unless it is needed.

  This doesn't turn `fs.open()` or `fsPromises.open()` into a synchronous
  blocking call. If synchronous operation is desired, something like
  `fs.openSync()` should be used.

* `'w'`: Open file for writing.
  The file is created (if it does not exist) or truncated (if it exists).

* `'wx'`: Like `'w'` but fails if the path exists.

* `'w+'`: Open file for reading and writing.
  The file is created (if it does not exist) or truncated (if it exists).

* `'wx+'`: Like `'w+'` but fails if the path exists.

`flag` can also be a number as documented by open(2); commonly used constants
are available from `fs.constants`. On Windows, flags are translated to
their equivalent ones where applicable, e.g. `O_WRONLY` to `FILE_GENERIC_WRITE`,
or `O_EXCL|O_CREAT` to `CREATE_NEW`, as accepted by `CreateFileW`.

The exclusive flag `'x'` (`O_EXCL` flag in open(2)) causes the operation to
return an error if the path already exists. On POSIX, if the path is a symbolic
link, using `O_EXCL` returns an error even if the link is to a path that does
not exist. The exclusive flag might not work with network file systems.

On Linux, positional writes don't work when the file is opened in append mode.
The kernel ignores the position argument and always appends the data to
the end of the file.

Modifying a file rather than replacing it may require the `flag` option to be
set to `'r+'` rather than the default `'w'`.

The behavior of some flags are platform-specific. As such, opening a directory
on macOS and Linux with the `'a+'` flag, as in the example below, will return an
error. In contrast, on Windows and FreeBSD, a file descriptor or a `FileHandle`
will be returned.

```js
// macOS and Linux
fs.open('<directory>', 'a+', (err, fd) => {
  // => [Error: EISDIR: illegal operation on a directory, open <directory>]
});

// Windows and FreeBSD
fs.open('<directory>', 'a+', (err, fd) => {
  // => null, <fd>
});
```

On Windows, opening an existing hidden file using the `'w'` flag (either
through `fs.open()`, `fs.writeFile()`, or `fsPromises.open()`) will fail with
`EPERM`. Existing hidden files can be opened for writing with the `'r+'` flag.

A call to `fs.ftruncate()` or `filehandle.truncate()` can be used to reset
the file contents.

[#25741]: https://github.com/nodejs/node/issues/25741
[Common System Errors]: errors.md#common-system-errors
[FS constants]: #fs-constants
[File access constants]: #file-access-constants
[MDN-Date]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date
[MDN-Number]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Number_type
[MSDN-Rel-Path]: https://docs.microsoft.com/en-us/windows/desktop/FileIO/naming-a-file#fully-qualified-vs-relative-paths
[MSDN-Using-Streams]: https://docs.microsoft.com/en-us/windows/desktop/FileIO/using-streams
[Naming Files, Paths, and Namespaces]: https://docs.microsoft.com/en-us/windows/desktop/FileIO/naming-a-file
[`AHAFS`]: https://developer.ibm.com/articles/au-aix_event_infrastructure/
[`Buffer.byteLength`]: buffer.md#static-method-bufferbytelengthstring-encoding
[`FSEvents`]: https://developer.apple.com/documentation/coreservices/file_system_events
[`Number.MAX_SAFE_INTEGER`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER
[`ReadDirectoryChangesW`]: https://docs.microsoft.com/en-us/windows/desktop/api/winbase/nf-winbase-readdirectorychangesw
[`UV_THREADPOOL_SIZE`]: cli.md#uv_threadpool_sizesize
[`event ports`]: https://illumos.org/man/port_create
[`filehandle.createReadStream()`]: #filehandlecreatereadstreamoptions
[`filehandle.createWriteStream()`]: #filehandlecreatewritestreamoptions
[`filehandle.writeFile()`]: #filehandlewritefiledata-options
[`fs.access()`]: #fsaccesspath-mode-callback
[`fs.accessSync()`]: #fsaccesssyncpath-mode
[`fs.chmod()`]: #fschmodpath-mode-callback
[`fs.chown()`]: #fschownpath-uid-gid-callback
[`fs.copyFile()`]: #fscopyfilesrc-dest-mode-callback
[`fs.createReadStream()`]: #fscreatereadstreampath-options
[`fs.createWriteStream()`]: #fscreatewritestreampath-options
[`fs.exists()`]: #fsexistspath-callback
[`fs.fstat()`]: #fsfstatfd-options-callback
[`fs.ftruncate()`]: #fsftruncatefd-len-callback
[`fs.futimes()`]: #fsfutimesfd-atime-mtime-callback
[`fs.lstat()`]: #fslstatpath-options-callback
[`fs.lutimes()`]: #fslutimespath-atime-mtime-callback
[`fs.mkdir()`]: #fsmkdirpath-options-callback
[`fs.mkdtemp()`]: #fsmkdtempprefix-options-callback
[`fs.open()`]: #fsopenpath-flags-mode-callback
[`fs.opendir()`]: #fsopendirpath-options-callback
[`fs.opendirSync()`]: #fsopendirsyncpath-options
[`fs.read()`]: #fsreadfd-buffer-offset-length-position-callback
[`fs.readFile()`]: #fsreadfilepath-options-callback
[`fs.readFileSync()`]: #fsreadfilesyncpath-options
[`fs.readdir()`]: #fsreaddirpath-options-callback
[`fs.readdirSync()`]: #fsreaddirsyncpath-options
[`fs.readv()`]: #fsreadvfd-buffers-position-callback
[`fs.realpath()`]: #fsrealpathpath-options-callback
[`fs.rm()`]: #fsrmpath-options-callback
[`fs.rmSync()`]: #fsrmsyncpath-options
[`fs.rmdir()`]: #fsrmdirpath-options-callback
[`fs.stat()`]: #fsstatpath-options-callback
[`fs.statfs()`]: #fsstatfspath-options-callback
[`fs.symlink()`]: #fssymlinktarget-path-type-callback
[`fs.utimes()`]: #fsutimespath-atime-mtime-callback
[`fs.watch()`]: #fswatchfilename-options-listener
[`fs.write(fd, buffer...)`]: #fswritefd-buffer-offset-length-position-callback
[`fs.write(fd, string...)`]: #fswritefd-string-position-encoding-callback
[`fs.writeFile()`]: #fswritefilefile-data-options-callback
[`fs.writev()`]: #fswritevfd-buffers-position-callback
[`fsPromises.access()`]: #fspromisesaccesspath-mode
[`fsPromises.open()`]: #fspromisesopenpath-flags-mode
[`fsPromises.opendir()`]: #fspromisesopendirpath-options
[`fsPromises.rm()`]: #fspromisesrmpath-options
[`fsPromises.stat()`]: #fspromisesstatpath-options
[`fsPromises.utimes()`]: #fspromisesutimespath-atime-mtime
[`inotify(7)`]: https://man7.org/linux/man-pages/man7/inotify.7.html
[`kqueue(2)`]: https://www.freebsd.org/cgi/man.cgi?query=kqueue&sektion=2
[`util.promisify()`]: util.md#utilpromisifyoriginal
[bigints]: https://tc39.github.io/proposal-bigint
[caveats]: #caveats
[chcp]: https://ss64.com/nt/chcp.html
[inode]: https://en.wikipedia.org/wiki/Inode
[support of file system `flags`]: #file-system-flags
