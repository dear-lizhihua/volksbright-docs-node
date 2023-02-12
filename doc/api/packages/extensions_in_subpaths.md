#### Extensions in subpaths

Package authors should provide either extensioned (`import 'pkg/subpath.js'`) or
extensionless (`import 'pkg/subpath'`) subpaths in their exports. This ensures
that there is only one subpath for each exported module so that all dependents
import the same consistent specifier, keeping the package contract clear for
consumers and simplifying package subpath completions.

Traditionally, packages tended to use the extensionless style, which has the
benefits of readability and of masking the true path of the file within the
package.

With [import maps][] now providing a standard for package resolution in browsers
and other JavaScript runtimes, using the extensionless style can result in
bloated import map definitions. Explicit file extensions can avoid this issue by
enabling the import map to utilize a [packages folder mapping][] to map multiple
subpaths where possible instead of a separate map entry per package subpath
export. This also mirrors the requirement of using [the full specifier path][]
in relative and absolute import specifiers.
