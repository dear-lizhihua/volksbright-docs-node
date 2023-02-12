### DEP0104: `process.env` string coercion

<!-- YAML
changes:
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18990
    description: Documentation-only deprecation.
-->

Type: Documentation-only (supports [`--pending-deprecation`][])

When assigning a non-string property to [`process.env`][], the assigned value is
implicitly converted to a string. This behavior is deprecated if the assigned
value is not a string, boolean, or number. In the future, such assignment might
result in a thrown error. Please convert the property to a string before
assigning it to `process.env`.
