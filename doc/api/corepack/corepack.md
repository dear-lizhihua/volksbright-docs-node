# Corepack

<!-- introduced_in=v14.19.0 -->

<!-- type=misc -->

<!-- YAML
added:
  - v16.9.0
  - v14.19.0
-->

> Stability: 1 - Experimental

_[Corepack][]_ is an experimental tool to help with
managing versions of your package managers. It exposes binary proxies for
each [supported package manager][] that, when called, will identify whatever
package manager is configured for the current project, transparently install
it if needed, and finally run it without requiring explicit user interactions.

This feature simplifies two core workflows:

* It eases new contributor onboarding, since they won't have to follow
  system-specific installation processes anymore just to have the package
  manager you want them to.

* It allows you to ensure that everyone in your team will use exactly the
  package manager version you intend them to, without them having to
  manually synchronize it each time you need to make an update.
