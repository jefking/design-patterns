# Event-Based Asynchronous Pattern Agent

When this file is included in a prompt, prefer Event-Based Asynchronous only
when asynchronous work should report progress, completion, and errors through
events or callbacks.

## Intent

Expose asynchronous operations through event notifications so callers can react
without blocking the initiating thread.

## Apply When

- Operations are long-running and need progress or completion notifications.
- The environment uses event loops, UI dispatchers, or callback-based async APIs.
- Callers may subscribe, unsubscribe, or marshal callbacks to a specific context.
- Cancellation and error delivery can be made explicit.

## Do Not Force It When

- Promises, futures, async/await, streams, or channels are clearer locally.
- Event ordering and lifetime cannot be guaranteed.
- Multiple subscribers would make ownership of results ambiguous.
- The operation is short and synchronous.

## Agent Directives

- Define event types for start, progress, completion, cancellation, and failure as needed.
- Specify callback thread or execution context.
- Make subscription and unsubscription lifecycle explicit.
- Prevent events after disposal unless explicitly allowed.
- Preserve error details without throwing on background threads unnoticed.

## Output Expectations

- Name the async operation and emitted events.
- Show subscription, cancellation, and completion handling.
- State ordering and threading guarantees.
- Include tests for success, progress, failure, cancellation, and unsubscribe behavior.

## Review Checklist

- Events are the idiomatic async surface for the codebase.
- Callback lifecycle is safe.
- Errors and cancellation reach callers.
- Event order is documented and testable.
