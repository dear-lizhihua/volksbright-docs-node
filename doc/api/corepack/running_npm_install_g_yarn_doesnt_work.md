### Running `npm install -g yarn` doesn't work

npm prevents accidentally overriding the Corepack binaries when doing a global
install. To avoid this problem, consider one of the following options:

* Don't run this command; Corepack will provide the package manager
  binaries anyway and will ensure that the requested versions are always
  available, so installing the package managers explicitly isn't needed.

* Add the `--force` flag to `npm install`; this will tell npm that it's fine to
  override binaries, but you'll erase the Corepack ones in the process. (Run
  [`corepack enable`][] to add them back.)

[Corepack]: https://github.com/nodejs/corepack
[Corepack documentation]: https://github.com/nodejs/corepack#readme
[Corepack repository]: https://github.com/nodejs/corepack
[Yarn]: https://yarnpkg.com
[`"packageManager"`]: packages.md#packagemanager
[`corepack disable`]: https://github.com/nodejs/corepack#corepack-disable--name
[`corepack enable`]: https://github.com/nodejs/corepack#corepack-enable--name
[`corepack prepare`]: https://github.com/nodejs/corepack#corepack-prepare--nameversion
[`package.json`]: packages.md#nodejs-packagejson-field-definitions
[pnpm]: https://pnpm.js.org
[supported binaries]: #supported-package-managers
[supported package manager]: #supported-package-managers
[various flags]: https://github.com/nodejs/corepack#utility-commands
