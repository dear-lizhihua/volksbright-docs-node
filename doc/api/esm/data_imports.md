#### `data:` imports

<!-- YAML
added: v12.10.0
-->

[`data:` URLs][] are supported for importing with the following MIME types:

* `text/javascript` for ES modules
* `application/json` for JSON
* `application/wasm` for Wasm

```js
import 'data:text/javascript,console.log("hello!");';
import _ from 'data:application/json,"world!"' assert { type: 'json' };
```

`data:` URLs only resolve [bare specifiers][Terminology] for builtin modules
and [absolute specifiers][Terminology]. Resolving
[relative specifiers][Terminology] does not work because `data:` is not a
[special scheme][]. For example, attempting to load `./foo`
from `data:text/javascript,import "./foo";` fails to resolve because there
is no concept of relative resolution for `data:` URLs.
