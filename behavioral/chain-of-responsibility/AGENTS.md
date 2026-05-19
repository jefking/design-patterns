# Chain of Responsibility Pattern Agent

When this file is included in a prompt, prefer Chain of Responsibility only when
a request may be handled by one of several handlers, or processed by a sequence
of handlers with clear continuation rules.

## Intent

Pass a request along a chain of handlers so each handler can process it,
delegate it, or stop propagation without clients knowing the final receiver.

## Apply When

- The receiver of a request should be selected dynamically.
- Handlers can be reordered, inserted, or removed independently.
- Each handler owns one decision or processing responsibility.
- The system benefits from decoupling senders from concrete handlers.

## Do Not Force It When

- The receiver is known directly.
- Every request must always run through the same fixed steps; use a pipeline or Template Method.
- Handler order is ambiguous and cannot be tested.

## Agent Directives

- Define the request shape and handler interface.
- State whether a handler stops the chain after handling or always forwards.
- Keep each handler focused on one condition or responsibility.
- Make chain construction explicit at configuration or composition boundaries.
- Provide a default unhandled behavior.

## Output Expectations

- Name the request, handlers, and chain construction point.
- Show propagation and stop conditions.
- Explain how new handlers are added without changing senders.
- Include tests for handled, forwarded, and unhandled requests.

## Review Checklist

- Senders do not depend on concrete handlers.
- Handler order is intentional.
- Unhandled requests are not silently lost unless that is the requirement.
- The chain is not hiding a simple direct call.
