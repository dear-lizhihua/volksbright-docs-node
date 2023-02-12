### DEP0166: Double slashes in imports and exports targets

<!-- YAML
changes:
  - version: v19.0.0
    pr-url: https://github.com/nodejs/node/pull/44495
    description: Runtime deprecation.
  - version: v18.10.0
    pr-url: https://github.com/nodejs/node/pull/44477
    description: Documentation-only deprecation
                 with `--pending-deprecation` support.
-->

Type: Runtime

Package imports and exports targets mapping into paths including a double slash
(of _"/"_ or _"\\"_) are deprecated and will fail with a resolution validation
error in a future release. This same deprecation also applies to pattern matches
starting or ending in a slash.
