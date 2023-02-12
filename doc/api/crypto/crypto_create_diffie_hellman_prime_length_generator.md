### `crypto.createDiffieHellman(primeLength[, generator])`

<!-- YAML
added: v0.5.0
-->

* `primeLength` {number}
* `generator` {number} **Default:** `2`
* Returns: {DiffieHellman}

Creates a `DiffieHellman` key exchange object and generates a prime of
`primeLength` bits using an optional specific numeric `generator`.
If `generator` is not specified, the value `2` is used.
