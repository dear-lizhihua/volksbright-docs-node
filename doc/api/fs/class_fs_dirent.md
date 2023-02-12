### Class: `fs.Dirent`

<!-- YAML
added: v10.10.0
-->

A representation of a directory entry, which can be a file or a subdirectory
within the directory, as returned by reading from an {fs.Dir}. The
directory entry is a combination of the file name and file type pairs.

Additionally, when [`fs.readdir()`][] or [`fs.readdirSync()`][] is called with
the `withFileTypes` option set to `true`, the resulting array is filled with
{fs.Dirent} objects, rather than strings or {Buffer}s.
