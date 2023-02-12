# Load the generated snapshot and start the application from index.js.
$ node --snapshot-blob snapshot.blob index.js
I am from the snapshot
```

The [`v8.startupSnapshot` API][] can be used to specify an entry point at
snapshot building time, thus avoiding the need of an additional entry
script at deserialization time:

```console
$ echo "require('v8').startupSnapshot.setDeserializeMainFunction(() => console.log('I am from the snapshot'))" > snapshot.js
$ node --snapshot-blob snapshot.blob --build-snapshot snapshot.js
$ node --snapshot-blob snapshot.blob
I am from the snapshot
```

For more information, check out the [`v8.startupSnapshot` API][] documentation.

Currently the support for run-time snapshot is experimental in that:

1. User-land modules are not yet supported in the snapshot, so only
   one single file can be snapshotted. Users can bundle their applications
   into a single script with their bundler of choice before building
   a snapshot, however.
2. Only a subset of the built-in modules work in the snapshot, though the
   Node.js core test suite checks that a few fairly complex applications
   can be snapshotted. Support for more modules are being added. If any
   crashes or buggy behaviors occur when building a snapshot, please file
   a report in the [Node.js issue tracker][] and link to it in the
   [tracking issue for user-land snapshots][].
