# Template Method Pattern Agent

When this file is included in a prompt, prefer the Template Method pattern only
when a stable algorithm skeleton should be shared while selected steps vary in
subclasses.

## Intent

Define the fixed sequence of an algorithm in a base type and let subclasses
customize specific steps.

## Apply When

- Several variants follow the same ordered workflow.
- The invariant parts of the workflow must stay centralized.
- Hooks or overridable steps are a natural fit for the language and codebase.
- Subclasses should vary steps, not the overall sequence.

## Do Not Force It When

- Composition, Strategy, or callbacks would be simpler and more flexible.
- The inheritance hierarchy is unstable.
- Subclasses need to reorder the algorithm frequently.

## Agent Directives

- Make the template method final or otherwise hard to bypass when the language supports it.
- Name required steps and optional hooks clearly.
- Keep base-class shared behavior cohesive.
- Avoid deep inheritance hierarchies.
- Document which steps may be overridden and which invariants must be preserved.

## Output Expectations

- Show the template method sequence.
- Identify abstract steps, concrete shared steps, and optional hooks.
- Explain how subclasses extend behavior safely.
- Include tests for the base workflow order and at least one concrete variant.

## Review Checklist

- The algorithm order is stable and enforced.
- Subclasses cannot accidentally break required invariants.
- Inheritance is justified by the local design.
- Hook methods are minimal and understandable.
