### Upgrading the global versions

When running outside of an existing project (for example when running
`yarn init`), Corepack will by default use predefined versions roughly
corresponding to the latest stable releases from each tool. Those versions can
be overridden by running the [`corepack prepare`][] command along with the
package manager version you wish to set:

```bash
corepack prepare yarn@x.y.z --activate
```

Alternately, a tag or range may be used:

```bash
corepack prepare pnpm@latest --activate
corepack prepare yarn@stable --activate
```
