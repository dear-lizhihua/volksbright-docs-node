### Community Conditions Definitions

Condition strings other than the `"import"`, `"require"`, `"node"`,
`"node-addons"` and `"default"` conditions
[implemented in Node.js core](#conditional-exports) are ignored by default.

Other platforms may implement other conditions and user conditions can be
enabled in Node.js via the [`--conditions` / `-C` flag][].

Since custom package conditions require clear definitions to ensure correct
usage, a list of common known package conditions and their strict definitions
is provided below to assist with ecosystem coordination.

* `"types"` - can be used by typing systems to resolve the typing file for
  the given export. _This condition should always be included first._
* `"deno"` - indicates a variation for the Deno platform.
* `"browser"` - any web browser environment.
* `"react-native"` - will be matched by the React Native framework (all
  platforms). _To target React Native for Web, `"browser"` should be specified
  before this condition._
* `"development"` - can be used to define a development-only environment
  entry point, for example to provide additional debugging context such as
  better error messages when running in a development mode. _Must always be
  mutually exclusive with `"production"`._
* `"production"` - can be used to define a production environment entry
  point. _Must always be mutually exclusive with `"development"`._

New conditions definitions may be added to this list by creating a pull request
to the [Node.js documentation for this section][]. The requirements for listing
a new condition definition here are that:

* The definition should be clear and unambiguous for all implementers.
* The use case for why the condition is needed should be clearly justified.
* There should exist sufficient existing implementation usage.
* The condition name should not conflict with another condition definition or
  condition in wide usage.
* The listing of the condition definition should provide a coordination
  benefit to the ecosystem that wouldn't otherwise be possible. For example,
  this would not necessarily be the case for company-specific or
  application-specific conditions.

The above definitions may be moved to a dedicated conditions registry in due
course.
