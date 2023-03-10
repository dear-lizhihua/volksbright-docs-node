# C++ addons

<!--introduced_in=v0.10.0-->

<!-- type=misc -->

_Addons_ are dynamically-linked shared objects written in C++. The
[`require()`][require] function can load addons as ordinary Node.js modules.
Addons provide an interface between JavaScript and C/C++ libraries.

There are three options for implementing addons: Node-API, nan, or direct
use of internal V8, libuv, and Node.js libraries. Unless there is a need for
direct access to functionality which is not exposed by Node-API, use Node-API.
Refer to [C/C++ addons with Node-API](n-api.md) for more information on
Node-API.

When not using Node-API, implementing addons is complicated,
involving knowledge of several components and APIs:

* [V8][]: the C++ library Node.js uses to provide the
  JavaScript implementation. V8 provides the mechanisms for creating objects,
  calling functions, etc. V8's API is documented mostly in the
  `v8.h` header file (`deps/v8/include/v8.h` in the Node.js source
  tree), which is also available [online][v8-docs].

* [libuv][]: The C library that implements the Node.js event loop, its worker
  threads and all of the asynchronous behaviors of the platform. It also
  serves as a cross-platform abstraction library, giving easy, POSIX-like
  access across all major operating systems to many common system tasks, such
  as interacting with the file system, sockets, timers, and system events. libuv
  also provides a threading abstraction similar to POSIX threads for
  more sophisticated asynchronous addons that need to move beyond the
  standard event loop. Addon authors should
  avoid blocking the event loop with I/O or other time-intensive tasks by
  offloading work via libuv to non-blocking system operations, worker threads,
  or a custom use of libuv threads.

* Internal Node.js libraries. Node.js itself exports C++ APIs that addons can
  use, the most important of which is the `node::ObjectWrap` class.

* Node.js includes other statically linked libraries including OpenSSL. These
  other libraries are located in the `deps/` directory in the Node.js source
  tree. Only the libuv, OpenSSL, V8, and zlib symbols are purposefully
  re-exported by Node.js and may be used to various extents by addons. See
  [Linking to libraries included with Node.js][] for additional information.

All of the following examples are available for [download][] and may
be used as the starting-point for an addon.
