#### prebuildify

[prebuildify][] is a tool based on node-gyp. The advantage of prebuildify is
that the built binaries are bundled with the native addon when it's
uploaded to npm. The binaries are downloaded from npm and are immediately
available to the module user when the native addon is installed.
