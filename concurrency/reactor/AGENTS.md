# Reactor Pattern Agent

When this file is included in a prompt, prefer Reactor only when synchronous
event sources should be demultiplexed and dispatched through an event loop.

## Intent

Wait for events from handles or resources, demultiplex readiness, and dispatch
handlers without dedicating one thread per connection.

## Apply When

- Many sockets, file descriptors, timers, or handles need scalable I/O handling.
- Events can be processed through nonblocking operations.
- Handlers are short and should not block the event loop.
- Registration, deregistration, and backpressure can be managed.

## Do Not Force It When

- The platform already provides an event loop abstraction used by the codebase.
- Blocking work dominates and should run in worker pools.
- Handler ordering, cancellation, or resource lifetime cannot be controlled.
- A thread-per-session model is simpler and sufficient.

## Agent Directives

- Define handles, event types, demultiplexer, dispatcher, and handlers.
- Keep handlers nonblocking or explicitly offload blocking work.
- Specify registration, interest changes, and cleanup behavior.
- Handle backpressure, partial reads/writes, and errors explicitly.
- Preserve event-loop ownership of state touched by handlers.

## Output Expectations

- Show event registration and dispatch flow.
- State threading and nonblocking assumptions.
- Explain error, close, and backpressure handling.
- Include tests or integration checks for dispatch and handler cleanup where practical.

## Review Checklist

- Reactor reduces concurrency overhead for many event sources.
- Handlers do not block the loop unexpectedly.
- Resource registration and cleanup are correct.
- Backpressure and partial I/O are considered.
