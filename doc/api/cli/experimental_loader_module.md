### `--experimental-loader=module`

<!-- YAML
added: v8.8.0
changes:
  - version: v12.11.1
    pr-url: https://github.com/nodejs/node/pull/29752
    description: This flag was renamed from `--loader` to
                 `--experimental-loader`.
-->

Specify the `module` of a custom experimental [ECMAScript module loader][].
`module` may be any string accepted as an [`import` specifier][].
