### `--v8-pool-size=num`

<!-- YAML
added: v5.10.0
-->

Set V8's thread pool size which will be used to allocate background jobs.

If set to `0` then Node.js will choose an appropriate size of the thread pool
based on an estimate of the amount of parallelism.

The amount of parallelism refers to the number of computations that can be
carried out simultaneously in a given machine. In general, it's the same as the
amount of CPUs, but it may diverge in environments such as VMs or containers.
