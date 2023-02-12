# is equivalent to

node --trace-event-categories v8,node,node.async_hooks
```

Alternatively, trace events may be enabled using the `node:trace_events` module:

```js
const trace_events = require('node:trace_events');
const tracing = trace_events.createTracing({ categories: ['node.perf'] });
tracing.enable();  // Enable trace event capture for the 'node.perf' category

// do work

tracing.disable();  // Disable trace event capture for the 'node.perf' category
```

Running Node.js with tracing enabled will produce log files that can be opened
in the [`chrome://tracing`](https://www.chromium.org/developers/how-tos/trace-event-profiling-tool)
tab of Chrome.

The logging file is by default called `node_trace.${rotation}.log`, where
`${rotation}` is an incrementing log-rotation id. The filepath pattern can
be specified with `--trace-event-file-pattern` that accepts a template
string that supports `${rotation}` and `${pid}`:

```bash
node --trace-event-categories v8 --trace-event-file-pattern '${pid}-${rotation}.log' server.js
```

To guarantee that the log file is properly generated after signal events like
`SIGINT`, `SIGTERM`, or `SIGBREAK`, make sure to have the appropriate handlers
in your code, such as:

```js
process.on('SIGINT', function onSigint() {
  console.info('Received SIGINT.');
  process.exit(130);  // Or applicable exit code depending on OS and signal
});
```

The tracing system uses the same time source
as the one used by `process.hrtime()`.
However the trace-event timestamps are expressed in microseconds,
unlike `process.hrtime()` which returns nanoseconds.

The features from this module are not available in [`Worker`][] threads.
