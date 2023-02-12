### DEP0155: Trailing slashes in pattern specifier resolutions

<!-- YAML
changes:
  - version: v17.0.0
    pr-url: https://github.com/nodejs/node/pull/40117
    description: Runtime deprecation.
  - version: v16.10.0
    pr-url: https://github.com/nodejs/node/pull/40039
    description: Documentation-only deprecation
                 with `--pending-deprecation` support.
-->

Type: Runtime

The remapping of specifiers ending in `"/"` like `import 'pkg/x/'` is deprecated
for package `"exports"` and `"imports"` pattern resolutions.
