# Iterator Pattern Agent

When this file is included in a prompt, prefer the Iterator pattern only when
clients need controlled traversal without depending on a collection's internal
representation.

## Intent

Provide sequential access to elements while hiding traversal mechanics and the
underlying data structure.

## Apply When

- A collection has a custom, nested, remote, lazy, filtered, or expensive traversal.
- Multiple traversal strategies should be supported.
- Clients should not know how items are stored.
- Traversal needs consistent invalidation, ordering, or resource cleanup behavior.

## Do Not Force It When

- The language's built-in iteration protocol already solves the problem clearly.
- The collection is simple and exposing standard iteration is enough.
- Traversal requires broad random access rather than sequential progress.

## Agent Directives

- Use the language's native iterator protocol when available.
- Define ordering, filtering, laziness, and termination behavior.
- Keep collection internals private.
- Specify what happens if the collection changes during iteration.
- Close or release resources for remote or streaming iterators.

## Output Expectations

- Name the aggregate and iterator responsibilities.
- Show example iteration from client code.
- State traversal order and mutation behavior.
- Include tests for empty, single-item, multi-item, and boundary traversal cases.

## Review Checklist

- Clients do not depend on internal storage.
- The iterator is easy to use with local language idioms.
- Traversal edge cases are specified.
- Resource-owning iterators are closed or exhausted safely.
