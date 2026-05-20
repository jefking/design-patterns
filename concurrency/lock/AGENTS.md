# Lock Pattern Agent

When this file is included in a prompt, prefer Lock only when shared mutable
state must be protected from concurrent access and simpler ownership rules do
not remove the sharing.

## Intent

Serialize access to a critical section so concurrent operations cannot corrupt
shared state.

## Apply When

- Multiple threads or tasks can read and write shared mutable state.
- Critical sections are small and well-defined.
- Lock ordering, timeout, and failure behavior can be specified.
- Alternatives such as immutability, message passing, atomics, or ownership transfer are insufficient.

## Do Not Force It When

- State can be immutable, thread-local, or owned by one worker.
- An atomic operation or concurrent data structure solves the problem.
- Lock scope would include blocking I/O or long-running work.
- Deadlock risk cannot be controlled.

## Agent Directives

- Identify protected state and the lock that guards it.
- Keep critical sections minimal.
- Define lock ordering when more than one lock may be acquired.
- Use language-native lock guards, defer, or scope cleanup to release reliably.
- Avoid exposing protected state outside the lock.

## Output Expectations

- Name the lock and protected fields.
- Show lock acquisition and release path.
- State deadlock, timeout, and reentrancy assumptions.
- Include tests or stress checks for concurrent access when practical.

## Review Checklist

- Every access to protected state uses the same discipline.
- Lock scope is small and exception-safe.
- Deadlock ordering is documented where needed.
- A simpler concurrency model was considered.
