# Thread Pool Pattern Agent

When this file is included in a prompt, prefer Thread Pool only when many tasks
should share a bounded set of worker threads.

## Intent

Reuse worker threads to execute queued tasks while limiting concurrency and
thread creation overhead.

## Apply When

- Task volume is high or bursty.
- Creating a thread per task would be expensive or unsafe.
- Concurrency needs a configured upper bound.
- Queueing, rejection, cancellation, and shutdown policy can be specified.

## Do Not Force It When

- The runtime executor already provides the needed pool.
- Work is nonblocking async and should stay on an event loop.
- Tasks require dedicated thread affinity.
- Queue growth would hide overload instead of applying backpressure.

## Agent Directives

- Define task contract, worker count, queue type, and rejection behavior.
- Separate CPU-bound and I/O-bound pools when needed.
- Propagate context, cancellation, deadlines, and errors deliberately.
- Define graceful and immediate shutdown behavior.
- Avoid blocking the pool waiting for tasks queued to the same pool unless safe.

## Output Expectations

- Name pool purpose, size policy, and task type.
- Show submit, execute, failure, and shutdown behavior.
- State queue limits and rejection/backpressure behavior.
- Include tests for execution, saturation, cancellation, failure, and shutdown.

## Review Checklist

- Pool size and queue policy match workload.
- Errors are not swallowed.
- Shutdown does not leak threads or tasks.
- Built-in executors were used or considered.
