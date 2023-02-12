# Query string

<!--introduced_in=v0.1.25-->

> Stability: 2 - Stable

<!--name=querystring-->

<!-- source_link=lib/querystring.js -->

The `node:querystring` module provides utilities for parsing and formatting URL
query strings. It can be accessed using:

```js
const querystring = require('node:querystring');
```

`querystring` is more performant than {URLSearchParams} but is not a
standardized API. Use {URLSearchParams} when performance is not critical or
when compatibility with browser code is desirable.
