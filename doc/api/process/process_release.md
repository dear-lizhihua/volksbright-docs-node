## `process.release`

<!-- YAML
added: v3.0.0
changes:
  - version: v4.2.0
    pr-url: https://github.com/nodejs/node/pull/3212
    description: The `lts` property is now supported.
-->

* {Object}

The `process.release` property returns an `Object` containing metadata related
to the current release, including URLs for the source tarball and headers-only
tarball.

`process.release` contains the following properties:

* `name` {string} A value that will always be `'node'`.
* `sourceUrl` {string} an absolute URL pointing to a _`.tar.gz`_ file containing
  the source code of the current release.
* `headersUrl`{string} an absolute URL pointing to a _`.tar.gz`_ file containing
  only the source header files for the current release. This file is
  significantly smaller than the full source file and can be used for compiling
  Node.js native add-ons.
* `libUrl` {string|undefined} an absolute URL pointing to a _`node.lib`_ file
  matching the architecture and version of the current release. This file is
  used for compiling Node.js native add-ons. _This property is only present on
  Windows builds of Node.js and will be missing on all other platforms._
* `lts` {string|undefined} a string label identifying the [LTS][] label for this
  release. This property only exists for LTS releases and is `undefined` for all
  other release types, including _Current_ releases. Valid values include the
  LTS Release code names (including those that are no longer supported).
  * `'Fermium'` for the 14.x LTS line beginning with 14.15.0.
  * `'Gallium'` for the 16.x LTS line beginning with 16.13.0.
  * `'Hydrogen'` for the 18.x LTS line beginning with 18.12.0.
    For other LTS Release code names, see [Node.js Changelog Archive](https://github.com/nodejs/node/blob/HEAD/doc/changelogs/CHANGELOG_ARCHIVE.md)

<!-- eslint-skip -->

```js
{
  name: 'node',
  lts: 'Hydrogen',
  sourceUrl: 'https://nodejs.org/download/release/v18.12.0/node-v18.12.0.tar.gz',
  headersUrl: 'https://nodejs.org/download/release/v18.12.0/node-v18.12.0-headers.tar.gz',
  libUrl: 'https://nodejs.org/download/release/v18.12.0/win-x64/node.lib'
}
```

In custom builds from non-release versions of the source tree, only the
`name` property may be present. The additional properties should not be
relied upon to exist.
