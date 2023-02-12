#### `dir.read()`

<!-- YAML
added: v12.12.0
-->

* Returns: {Promise} containing {fs.Dirent|null}

Asynchronously read the next directory entry via readdir(3) as an
{fs.Dirent}.

A promise is returned that will be resolved with an {fs.Dirent}, or `null`
if there are no more directory entries to read.

Directory entries returned by this function are in no particular order as
provided by the operating system's underlying directory mechanisms.
Entries added or removed while iterating over the directory might not be
included in the iteration results.
