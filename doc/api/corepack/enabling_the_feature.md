### Enabling the feature

Due to its experimental status, Corepack currently needs to be explicitly
enabled to have any effect. To do that, run [`corepack enable`][], which
will set up the symlinks in your environment next to the `node` binary
(and overwrite the existing symlinks if necessary).

From this point forward, any call to the [supported binaries][] will work
without further setup. Should you experience a problem, run
[`corepack disable`][] to remove the proxies from your system (and consider
opening an issue on the [Corepack repository][] to let us know).
