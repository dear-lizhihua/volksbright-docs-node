### Class: `fs.FSWatcher`

<!-- YAML
added: v0.5.8
-->

* Extends {EventEmitter}

A successful call to [`fs.watch()`][] method will return a new {fs.FSWatcher}
object.

All {fs.FSWatcher} objects emit a `'change'` event whenever a specific watched
file is modified.
