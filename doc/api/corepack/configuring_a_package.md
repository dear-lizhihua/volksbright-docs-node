### Configuring a package

The Corepack proxies will find the closest [`package.json`][] file in your
current directory hierarchy to extract its [`"packageManager"`][] property.

If the value corresponds to a [supported package manager][], Corepack will make
sure that all calls to the relevant binaries are run against the requested
version, downloading it on demand if needed, and aborting if it cannot be
successfully retrieved.
