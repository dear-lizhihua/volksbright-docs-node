#### File URL paths

<!-- YAML
added: v7.6.0
-->

For most `node:fs` module functions, the `path` or `filename` argument may be
passed as a {URL} object using the `file:` protocol.

```mjs
import { readFileSync } from 'node:fs';

readFileSync(new URL('file:///tmp/hello'));
```

`file:` URLs are always absolute paths.
