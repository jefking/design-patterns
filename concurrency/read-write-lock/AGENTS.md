# Read-Write Lock Pattern Agent

When this file is included in a prompt, prefer Read-Write Lock only when many
readers can safely run in parallel while writers require exclusive access.

## Intent

Allow concurrent reads of shared state while serializing writes and excluding
readers during mutation.

## Apply When

- Read operations are frequent and writes are less frequent.
- Reads are long or expensive enough that parallelism matters.
- The protected state cannot be made immutable or copy-on-write cheaply.
- Starvation and upgrade behavior can be defined.

## Do Not Force It When

- Writes are frequent enough that a normal mutex is simpler and faster.
- Read sections may perform writes indirectly.
- Lock upgrades are needed but unsafe in the chosen primitive.
- A snapshot, immutable structure, or concurrent map solves the problem.

## Agent Directives

- Identify which operations take read versus write locks.
- Keep read-locked code side-effect free for protected state.
- Define writer priority, reader priority, fairness, and starvation expectations.
- Avoid lock upgrade patterns unless the primitive supports them safely.
- Release locks with scope guards, defer, or equivalent cleanup.

## Output Expectations

- Name protected state and lock mode for each operation.
- Show read and write access examples.
- State fairness and upgrade policy.
- Include tests or stress checks for concurrent reads and exclusive writes.

## Review Checklist

- Read-heavy workload justifies the extra complexity.
- Writes cannot occur under read locks.
- Starvation behavior is acceptable.
- A simpler mutex or immutable snapshot was considered.
