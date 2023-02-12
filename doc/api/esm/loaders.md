## Loaders

<!-- YAML
added: v8.8.0
changes:
  - version:
    - v18.6.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42623
    description: Add support for chaining loaders.
  - version: v16.12.0
    pr-url: https://github.com/nodejs/node/pull/37468
    description: Removed `getFormat`, `getSource`, `transformSource`, and
                 `globalPreload`; added `load` hook and `getGlobalPreload` hook.
-->

> Stability: 1 - Experimental

> This API is currently being redesigned and will still change.

<!-- type=misc -->

To customize the default module resolution, loader hooks can optionally be
provided via a `--experimental-loader ./loader-name.mjs` argument to Node.js.

When hooks are used they apply to each subsequent loader, the entry point, and
all `import` calls. They won't apply to `require` calls; those still follow
[CommonJS][] rules.

Loaders follow the pattern of `--require`:

```console
node \
  --experimental-loader unpkg \
  --experimental-loader http-to-https \
  --experimental-loader cache-buster
```

These are called in the following sequence: `cache-buster` calls
`http-to-https` which calls `unpkg`.
