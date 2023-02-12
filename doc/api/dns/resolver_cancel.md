### `resolver.cancel()`

<!-- YAML
added:
  - v15.3.0
  - v14.17.0
-->

Cancel all outstanding DNS queries made by this resolver. The corresponding
promises will be rejected with an error with the code `ECANCELLED`.
