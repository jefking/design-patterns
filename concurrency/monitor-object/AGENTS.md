# Monitor Object Pattern Agent

When this file is included in a prompt, prefer Monitor Object only when an
object should encapsulate shared state and synchronize all access through its
own methods.

## Intent

Protect an object's internal state by making its methods mutually exclusive and
coordinating wait conditions inside the object.

## Apply When

- Shared mutable state belongs inside one object.
- All state access can be routed through synchronized methods.
- The object may need condition waits in addition to mutual exclusion.
- Encapsulation is improved by combining state and synchronization policy.

## Do Not Force It When

- State can be owned by one actor, task, or thread instead.
- Locking each method would be too coarse or cause deadlocks.
- Clients need to compose multiple operations atomically outside the object.
- Existing concurrent collections or primitives solve the need.

## Agent Directives

- Keep protected state private.
- Synchronize every method that reads or writes protected state.
- Define condition wait, signal, timeout, and shutdown behavior.
- Avoid callbacks or external calls while holding the monitor lock.
- Document reentrancy assumptions for the language runtime.

## Output Expectations

- Name protected state and synchronized methods.
- Show one method that waits or mutates under the monitor.
- State lock granularity and condition behavior.
- Include tests for concurrent calls and wait/signal behavior when present.

## Review Checklist

- No protected state leaks unsynchronized.
- Monitor methods are cohesive and not overly broad.
- External calls do not happen while holding the lock.
- Wait conditions are checked safely.
