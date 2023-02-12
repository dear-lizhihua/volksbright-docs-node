## `querystring.parse(str[, sep[, eq[, options]]])`

<!-- YAML
added: v0.1.25
changes:
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/10967
    description: Multiple empty entries are now parsed correctly (e.g. `&=&=`).
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/6055
    description: The returned object no longer inherits from `Object.prototype`.
  - version:
    - v6.0.0
    - v4.2.4
    pr-url: https://github.com/nodejs/node/pull/3807
    description: The `eq` parameter may now have a length of more than `1`.
-->

* `str` {string} The URL query string to parse
* `sep` {string} The substring used to delimit key and value pairs in the
  query string. **Default:** `'&'`.
* `eq` {string}. The substring used to delimit keys and values in the
  query string. **Default:** `'='`.
* `options` {Object}
  * `decodeURIComponent` {Function} The function to use when decoding
    percent-encoded characters in the query string. **Default:**
    `querystring.unescape()`.
  * `maxKeys` {number} Specifies the maximum number of keys to parse.
    Specify `0` to remove key counting limitations. **Default:** `1000`.

The `querystring.parse()` method parses a URL query string (`str`) into a
collection of key and value pairs.

For example, the query string `'foo=bar&abc=xyz&abc=123'` is parsed into:

<!-- eslint-skip -->

```js
{
  foo: 'bar',
  abc: ['xyz', '123']
}
```

The object returned by the `querystring.parse()` method _does not_
prototypically inherit from the JavaScript `Object`. This means that typical
`Object` methods such as `obj.toString()`, `obj.hasOwnProperty()`, and others
are not defined and _will not work_.

By default, percent-encoded characters within the query string will be assumed
to use UTF-8 encoding. If an alternative character encoding is used, then an
alternative `decodeURIComponent` option will need to be specified:

```js
// Assuming gbkDecodeURIComponent function already exists...

querystring.parse('w=%D6%D0%CE%C4&foo=bar', null, null,
                  { decodeURIComponent: gbkDecodeURIComponent });
```
