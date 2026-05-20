# CPU Atomic Operation Pattern Agent

When this file is included in a prompt, prefer CPU Atomic Operation only when a
small shared value can be updated safely with atomic primitives instead of a
larger lock.

## Intent

Use hardware or runtime atomic operations to perform indivisible reads, writes,
or read-modify-write updates on shared values.

## Apply When

- The shared state is a simple counter, flag, pointer, reference, or state word.
- Atomic ordering requirements can be specified correctly.
- Lock-free behavior improves contention, latency, or signal-safety.
- Invariants do not span multiple non-atomic fields.

## Do Not Force It When

- Multiple fields must change together.
- Memory ordering is unclear.
- A mutex would be simpler and fast enough.
- The algorithm is lock-free only in name and hard to verify.

## Agent Directives

- Choose atomic types provided by the language/runtime.
- Define memory ordering: relaxed, acquire, release, acq-rel, or sequential consistency.
- Keep atomic invariants small and documented.
- Use compare-and-swap loops carefully with retry limits or progress reasoning when relevant.
- Avoid mixing atomic and non-atomic access to the same state.

## Output Expectations

- Name atomic fields and operations.
- State memory-ordering rationale.
- Show how callers observe or update the value.
- Include tests or stress checks for concurrent updates and visibility where practical.

## Review Checklist

- Atomic scope is small enough to reason about.
- Memory ordering is explicit and valid.
- No unsynchronized non-atomic access exists.
- A simple lock was considered and rejected for a concrete reason.
