# Observer Pattern Agent

When this file is included in a prompt, prefer the Observer pattern only when
subscribers need to react to subject changes without tight coupling to the
subject.

## Intent

Let a subject notify interested observers about events or state changes through
a subscription contract.

## Apply When

- Multiple consumers may react to the same event.
- The subject should not know concrete subscriber classes.
- Subscribers can be added or removed dynamically.
- Notifications represent meaningful domain or lifecycle events.

## Do Not Force It When

- Only one direct collaborator needs the result.
- Call order, transactions, or error handling require a tighter workflow.
- Events would be too fine-grained and noisy.

## Agent Directives

- Define event names and payloads from subscriber needs.
- Make subscription and unsubscription lifecycle explicit.
- Specify synchronous versus asynchronous delivery.
- Define ordering, error isolation, retries, and backpressure when relevant.
- Avoid exposing mutable subject internals through event payloads.

## Output Expectations

- Name the subject, observer contract, and event payloads.
- Show subscription and notification flow.
- Explain failure handling for observer callbacks.
- Include tests for subscribe, notify, unsubscribe, and observer failure behavior.

## Review Checklist

- Subject depends on observer contracts, not concrete observers.
- Subscribers can be removed to avoid leaks.
- Event payloads are stable and appropriately scoped.
- Notification semantics are deterministic enough for the use case.
