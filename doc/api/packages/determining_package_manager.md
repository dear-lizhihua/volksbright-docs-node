## Determining package manager

> Stability: 1 - Experimental

While all Node.js projects are expected to be installable by all package
managers once published, their development teams are often required to use one
specific package manager. To make this process easier, Node.js ships with a
tool called [Corepack][] that aims to make all package managers transparently
available in your environment - provided you have Node.js installed.

By default Corepack won't enforce any specific package manager and will use
the generic "Last Known Good" versions associated with each Node.js release,
but you can improve this experience by setting the [`"packageManager"`][] field
in your project's `package.json`.
