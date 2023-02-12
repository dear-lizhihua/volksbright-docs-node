### `"packageManager"`

<!-- YAML
added:
  - v16.9.0
  - v14.19.0
-->

> Stability: 1 - Experimental

* Type: {string}

```json
{
  "packageManager": "<package manager name>@<version>"
}
```

The `"packageManager"` field defines which package manager is expected to be
used when working on the current project. It can be set to any of the
[supported package managers][], and will ensure that your teams use the exact
same package manager versions without having to install anything else other than
Node.js.

This field is currently experimental and needs to be opted-in; check the
[Corepack][] page for details about the procedure.
