### Offline workflow

Many production environments don't have network access. Since Corepack
usually downloads the package manager releases straight from their registries,
it can conflict with such environments. To avoid that happening, call the
[`corepack prepare`][] command while you still have network access (typically at
the same time you're preparing your deploy image). This will ensure that the
required package managers are available even without network access.

The `prepare` command has [various flags][]. Consult the detailed
[Corepack documentation][] for more information.
