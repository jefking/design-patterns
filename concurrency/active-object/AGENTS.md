# Active Object Pattern Agent

When this file is included in a prompt, prefer Active Object only when method
invocation should be decoupled from execution on a separate thread or event loop.

## Intent

Turn calls into queued requests so a scheduler can execute them asynchronously
inside the active object's own control context.

## Apply When

- A component must serialize access to its internal state.
- Callers should receive futures, promises, callbacks, or messages instead of blocking.
- Work must run on a dedicated thread, actor, event loop, or executor.
- Scheduling, cancellation, and shutdown behavior can be defined.

## Do Not Force It When

- Direct async functions or actors already solve the problem idiomatically.
- Work is cheap and synchronous calls are easier.
- Callers need immediate transactional results.
- Queue growth, cancellation, or shutdown cannot be handled safely.

## Agent Directives

- Define the proxy API, request object, scheduler, and servant/executor role.
- Preserve ordering guarantees deliberately.
- Define future completion, failure propagation, cancellation, and timeouts.
- Make shutdown drain, reject, or cancel queued work explicitly.
- Protect internal state by executing it only in the active context.

## Output Expectations

- Show call submission and asynchronous result handling.
- State ordering, concurrency, and backpressure behavior.
- Explain shutdown semantics.
- Include tests for ordering, failure propagation, cancellation, and shutdown.

## Review Checklist

- Invocation and execution are truly decoupled.
- Internal state is accessed only from the intended execution context.
- Queue behavior is bounded or monitored.
- Async errors reach callers predictably.
