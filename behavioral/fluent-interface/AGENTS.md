# Fluent Interface Pattern Agent

When this file is included in a prompt, prefer Fluent Interface only when chained
method calls make a configuration, query, or domain operation easier to read
without hiding invalid states.

## Intent

Design an API whose calls chain in a readable sequence, often resembling a small
domain-specific language.

## Apply When

- Callers configure or compose an object through multiple related steps.
- Method chaining improves readability over many temporary variables.
- The chain can guide valid order or valid combinations.
- The result is built, executed, or materialized at a clear terminal method.

## Do Not Force It When

- Chaining hides side effects or delayed execution.
- Ordinary constructors, options objects, or function calls are clearer.
- Invalid intermediate states cannot be prevented or reported well.
- The fluent API would be harder to debug than direct calls.

## Agent Directives

- Make each chained method return the next useful context deliberately.
- Use domain verbs and nouns, not generic setter noise.
- Separate configuration steps from terminal execution or build methods.
- Define mutability: immutable chain steps, mutable builder, or staged types.
- Surface validation errors at the earliest useful point.

## Output Expectations

- Show a representative call chain.
- Name the terminal method and result type.
- State whether the chain is mutable, immutable, or staged.
- Include tests for valid chains, invalid order, and terminal behavior.

## Review Checklist

- The chain reads better than equivalent direct calls.
- Side effects and execution timing are obvious.
- Invalid states are prevented or clearly reported.
- The API does not become a large pseudo-language without need.
