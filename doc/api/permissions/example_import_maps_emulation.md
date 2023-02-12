##### Example: [import maps][] emulation

Given an import map:

```json
{
  "imports": {
    "react": "./app/node_modules/react/index.js"
  },
  "scopes": {
    "./ssr/": {
      "react": "./app/node_modules/server-side-react/index.js"
    }
  }
}
```

```json
{
  "dependencies": true,
  "scopes": {
    "": {
      "cascade": true,
      "dependencies": {
        "react": "./app/node_modules/react/index.js"
      }
    },
    "./ssr/": {
      "cascade": true,
      "dependencies": {
        "react": "./app/node_modules/server-side-react/index.js"
      }
    }
  }
}
```

Import maps assume you can get any resource by default. This means
`"dependencies"` at the top level of the policy should be set to `true`.
Policies require this to be opt-in since it enables all resources of the
application cross linkage which doesn't make sense for many scenarios. They also
assume any given scope has access to any scope above its allowed dependencies;
all scopes emulating import maps must set `"cascade": true`.

Import maps only have a single top level scope for their "imports". So for
emulating `"imports"` use the `""` scope. For emulating `"scopes"` use the
`"scopes"` in a similar manner to how `"scopes"` works in import maps.

Caveats: Policies do not use string matching for various finding of scope. They
do URL traversals. This means things like `blob:` and `data:` URLs might not be
entirely interoperable between the two systems. For example import maps can
partially match a `data:` or `blob:` URL by partitioning the URL on a `/`
character, policies intentionally cannot. For `blob:` URLs import map scopes do
not adopt the origin of the `blob:` URL.

Additionally, import maps only work on `import` so it may be desirable to add a
`"import"` condition to all dependency mappings.

[Security Policy]: https://github.com/nodejs/node/blob/main/SECURITY.md
[import maps]: https://url.spec.whatwg.org/#relative-url-with-fragment-string
[relative-url string]: https://url.spec.whatwg.org/#relative-url-with-fragment-string
[special schemes]: https://url.spec.whatwg.org/#special-scheme
