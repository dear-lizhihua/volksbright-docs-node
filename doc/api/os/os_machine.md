## `os.machine()`

<!-- YAML
added:
  - v18.9.0
  - v16.18.0
-->

* Returns {string}

Returns the machine type as a string, such as `arm`, `arm64`, `aarch64`,
`mips`, `mips64`, `ppc64`, `ppc64le`, `s390`, `s390x`, `i386`, `i686`, `x86_64`.

On POSIX systems, the machine type is determined by calling
[`uname(3)`][]. On Windows, `RtlGetVersion()` is used, and if it is not
available, `GetVersionExW()` will be used. See
<https://en.wikipedia.org/wiki/Uname#Examples> for more information.
