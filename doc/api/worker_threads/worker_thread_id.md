## `worker.threadId`

<!-- YAML
added: v10.5.0
-->

* {integer}

An integer identifier for the current thread. On the corresponding worker object
(if there is any), it is available as [`worker.threadId`][].
This value is unique for each [`Worker`][] instance inside a single process.
