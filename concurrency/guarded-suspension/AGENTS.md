# Guarded Suspension Pattern Agent

When this file is included in a prompt, prefer Guarded Suspension only when an
operation must wait until a state condition becomes true.

## Intent

Suspend execution while a guarded precondition is false, then resume when another
thread or task signals that the condition may be satisfied.

## Apply When

- An operation cannot proceed until a shared state condition is true.
- Waiting is correct and bounded by cancellation, timeout, or shutdown behavior.
- A condition variable, monitor, channel, semaphore, or async primitive is available.
- The guard can be checked atomically with wait registration.

## Do Not Force It When

- The correct behavior is immediate skip or rejection; use Balking.
- Busy waiting would be used instead of a proper blocking primitive.
- No timeout, cancellation, or shutdown path exists for potentially indefinite waits.
- The guarded condition cannot be expressed clearly.

## Agent Directives

- Define the guarded condition in code, not only in comments.
- Check the condition in a loop around waits to handle spurious wakeups.
- Signal waiters whenever state changes may satisfy the guard.
- Define timeout, cancellation, interruption, and shutdown behavior.
- Avoid holding locks while performing long work after the guard passes.

## Output Expectations

- Show the guard, wait, signal, and proceed paths.
- State timeout and cancellation behavior.
- Explain synchronization primitive choice.
- Include tests for immediate proceed, wait-then-proceed, timeout, and shutdown.

## Review Checklist

- Waiting is semantically required.
- Guard checks are race-safe.
- Spurious wakeups and missed signals are handled.
- Waits cannot hang indefinitely unless that is explicit.
