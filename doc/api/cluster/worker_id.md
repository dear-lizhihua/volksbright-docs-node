### `worker.id`

<!-- YAML
added: v0.8.0
-->

* {integer}

Each new worker is given its own unique id, this id is stored in the
`id`.

While a worker is alive, this is the key that indexes it in
`cluster.workers`.
