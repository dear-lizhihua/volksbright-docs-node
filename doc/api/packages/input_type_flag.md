### `--input-type` flag

<!-- YAML
added: v12.0.0
-->

Strings passed in as an argument to `--eval` (or `-e`), or piped to `node` via
`STDIN`, are treated as [ES modules][] when the `--input-type=module` flag
is set.

```bash
node --input-type=module --eval "import { sep } from 'node:path'; console.log(sep);"

echo "import { sep } from 'node:path'; console.log(sep);" | node --input-type=module
```

For completeness there is also `--input-type=commonjs`, for explicitly running
string input as CommonJS. This is the default behavior if `--input-type` is
unspecified.
