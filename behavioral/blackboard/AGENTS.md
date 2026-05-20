# Blackboard Pattern Agent

When this file is included in a prompt, prefer Blackboard only when independent
knowledge sources need to collaborate through a shared problem state.

## Intent

Coordinate multiple specialized contributors through a shared blackboard where
partial results are posted, inspected, and refined until a solution emerges.

## Apply When

- The solution requires several independent algorithms, rules, agents, or analyzers.
- Contributors can work from shared intermediate state without direct coupling.
- A controller can decide which contributor should run next.
- The problem is exploratory, incremental, or opportunistic rather than a fixed pipeline.

## Do Not Force It When

- A simple sequence of steps is known in advance.
- Shared mutable state would make correctness or concurrency unclear.
- Contributors need tight request/response coordination.
- An event bus, pipeline, or workflow engine matches the flow better.

## Agent Directives

- Define the blackboard data model and ownership of updates.
- Define knowledge-source contracts and activation conditions.
- Keep contributors independent; communicate through the blackboard, not direct calls.
- Specify controller scheduling, conflict resolution, and termination behavior.
- Guard shared state with transactions, locks, or snapshots when concurrent.

## Output Expectations

- Name the blackboard, knowledge sources, and controller.
- Show how contributors read, write, and signal progress.
- State stopping criteria and conflict handling.
- Include tests for contributor activation, shared-state updates, and convergence or failure.

## Review Checklist

- The problem benefits from opportunistic collaboration.
- Shared state has a clear schema and concurrency policy.
- Contributors stay decoupled.
- Termination and failure behavior are defined.
