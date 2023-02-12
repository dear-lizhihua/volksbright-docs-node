### Network-based loading is not enabled by default

For now, the `--experimental-network-imports` flag is required to enable loading
resources over `http:` or `https:`. In the future, a different mechanism will be
used to enforce this. Opt-in is required to prevent transitive dependencies
inadvertently using potentially mutable state that could affect reliability
of Node.js applications.

<i id="esm_experimental_loaders"></i>
