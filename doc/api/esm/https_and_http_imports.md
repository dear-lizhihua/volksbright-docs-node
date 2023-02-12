## HTTPS and HTTP imports

> Stability: 1 - Experimental

Importing network based modules using `https:` and `http:` is supported under
the `--experimental-network-imports` flag. This allows web browser-like imports
to work in Node.js with a few differences due to application stability and
security concerns that are different when running in a privileged environment
instead of a browser sandbox.
