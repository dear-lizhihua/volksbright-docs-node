### `-C condition`, `--conditions=condition`

<!-- YAML
added:
  - v14.9.0
  - v12.19.0
-->

> Stability: 1 - Experimental

Enable experimental support for custom [conditional exports][] resolution
conditions.

Any number of custom string condition names are permitted.

The default Node.js conditions of `"node"`, `"default"`, `"import"`, and
`"require"` will always apply as defined.

For example, to run a module with "development" resolutions:

```console
$ node -C development app.js
```
