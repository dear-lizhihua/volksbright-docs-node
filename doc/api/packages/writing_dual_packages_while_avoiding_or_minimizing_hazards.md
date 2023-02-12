### Writing dual packages while avoiding or minimizing hazards

First, the hazard described in the previous section occurs when a package
contains both CommonJS and ES module sources and both sources are provided for
use in Node.js, either via separate main entry points or exported paths. A
package might instead be written where any version of Node.js receives only
CommonJS sources, and any separate ES module sources the package might contain
are intended only for other environments such as browsers. Such a package
would be usable by any version of Node.js, since `import` can refer to CommonJS
files; but it would not provide any of the advantages of using ES module syntax.

A package might also switch from CommonJS to ES module syntax in a [breaking
change](https://semver.org/) version bump. This has the disadvantage that the
newest version of the package would only be usable in ES module-supporting
versions of Node.js.

Every pattern has tradeoffs, but there are two broad approaches that satisfy the
following conditions:

1. The package is usable via both `require` and `import`.
2. The package is usable in both current Node.js and older versions of Node.js
   that lack support for ES modules.
3. The package main entry point, e.g. `'pkg'` can be used by both `require` to
   resolve to a CommonJS file and by `import` to resolve to an ES module file.
   (And likewise for exported paths, e.g. `'pkg/feature'`.)
4. The package provides named exports, e.g. `import { name } from 'pkg'` rather
   than `import pkg from 'pkg'; pkg.name`.
5. The package is potentially usable in other ES module environments such as
   browsers.
6. The hazards described in the previous section are avoided or minimized.
