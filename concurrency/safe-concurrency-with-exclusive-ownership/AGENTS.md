# Safe Concurrency With Exclusive Ownership Pattern Agent

When this file is included in a prompt, prefer Safe Concurrency with Exclusive
Ownership only when concurrency safety can be achieved by proving one owner has
mutation rights at a time.

## Intent

Avoid runtime locking by structuring ownership so mutable state is accessed
exclusively or shared only immutably.

## Apply When

- The language supports ownership, borrowing, move semantics, immutability, or linear types.
- State can be partitioned so each worker owns its part.
- Sharing can be replaced by message passing, snapshots, or immutable references.
- Compile-time or structural rules can prevent data races.

## Do Not Force It When

- The runtime cannot enforce or make ownership rules visible.
- Shared mutation is inherent and needs synchronization.
- Ownership transfer would make the design much harder to understand.
- External APIs require shared mutable handles.

## Agent Directives

- Identify the owner of every mutable piece of state.
- Prefer immutable sharing and explicit ownership transfer.
- Use channels, queues, moves, or scoped borrows to hand off data.
- Avoid aliasing mutable references across concurrent boundaries.
- Document any unsafe escape hatches and keep them isolated.

## Output Expectations

- Name owned state and ownership boundary.
- Show ownership transfer or immutable sharing path.
- Explain why locks are unnecessary.
- Include compile-time checks, type tests, or concurrency tests where practical.

## Review Checklist

- Mutable state has one owner at a time.
- Shared references are immutable or synchronized.
- Ownership transfer is explicit and understandable.
- Any unsafe code is minimal and justified.
