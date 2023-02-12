### `script.cachedDataRejected`

<!-- YAML
added: v5.7.0
-->

* {boolean|undefined}

When `cachedData` is supplied to create the `vm.Script`, this value will be set
to either `true` or `false` depending on acceptance of the data by V8.
Otherwise the value is `undefined`.
