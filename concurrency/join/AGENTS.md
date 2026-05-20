# Join Pattern Agent

When this file is included in a prompt, prefer Join only when progress requires
coordination across multiple messages, tasks, or concurrent branches.

## Intent

Wait for or react to a defined combination of asynchronous events before running
the next action.

## Apply When

- A workflow needs results from several concurrent operations.
- Message combinations, barriers, rendezvous, or join patterns are central to the design.
- Partial completion, timeout, cancellation, and failure behavior can be defined.
- Results must be combined once all required inputs arrive.

## Do Not Force It When

- Operations are independent and do not need coordination.
- A simple sequential call is clearer.
- Existing promise combinators, task groups, or structured concurrency primitives solve it.
- Partial failure semantics are unknown.

## Agent Directives

- Define which branches, messages, or tasks must join.
- Specify all-success, any-success, quorum, timeout, and failure behavior.
- Preserve cancellation propagation.
- Avoid unbounded accumulation of unmatched messages or task handles.
- Use structured concurrency primitives when available.

## Output Expectations

- Show concurrent start and join point.
- State result-combination and failure rules.
- Explain timeout and cancellation behavior.
- Include tests for all-complete, partial failure, timeout, and cancellation.

## Review Checklist

- Coordination requirement is real.
- Join semantics are explicit.
- Resources from losing or failed branches are cleaned up.
- Built-in structured concurrency was considered.
