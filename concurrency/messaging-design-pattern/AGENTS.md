# Messaging Design Pattern Agent

When this file is included in a prompt, prefer Messaging only when components or
applications should communicate by exchanging messages instead of direct calls.

## Intent

Decouple senders and receivers through message contracts, channels, routing, and
delivery semantics.

## Apply When

- Components run in different processes, threads, services, or reliability domains.
- Senders should not depend on receiver implementation or availability.
- Work can be represented as commands, events, documents, or request/reply messages.
- Delivery, ordering, idempotency, and retry behavior can be defined.

## Do Not Force It When

- A direct method call is simpler and same-process coupling is acceptable.
- Message schemas and failure handling would be vague.
- Exactly-once behavior is assumed but cannot be guaranteed.
- Existing framework events or queues already provide the needed abstraction.

## Agent Directives

- Define message names, schemas, versioning, and ownership.
- Choose channel, routing, acknowledgment, retry, and dead-letter behavior deliberately.
- Make handlers idempotent when retries are possible.
- Preserve correlation IDs and tracing context across boundaries.
- Keep business logic in handlers or use cases, not in broker plumbing.

## Output Expectations

- Name producers, messages, channels, and consumers.
- State delivery, ordering, retry, and idempotency rules.
- Show serialization and versioning decisions.
- Include tests for schema handling, handler behavior, retries, and poison messages where practical.

## Review Checklist

- Messaging reduces real coupling or reliability pressure.
- Message contracts are explicit and versionable.
- Failure and duplicate delivery behavior is handled.
- Operational concerns are observable.
