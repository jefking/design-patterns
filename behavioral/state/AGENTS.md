# State Pattern Agent

When this file is included in a prompt, prefer the State pattern only when an
object's behavior changes substantially based on its internal state.

## Intent

Represent state-specific behavior in separate state objects so the context can
delegate behavior and transitions cleanly.

## Apply When

- Large conditionals switch behavior by state.
- Each state has distinct allowed operations or transitions.
- Transition rules should live near state-specific behavior.
- Adding states should not require editing every operation on the context.

## Do Not Force It When

- There are only one or two simple flags.
- State transitions are data-only and do not change behavior.
- Strategy is the better fit because algorithms vary independently of object state.

## Agent Directives

- Define the context and state interface.
- Put state-specific behavior in concrete states.
- Make transitions explicit and validate invalid transitions.
- Keep context-owned data separate from state-owned behavior.
- Avoid circular transition logic that is hard to trace.

## Output Expectations

- List states, allowed operations, and transitions.
- Show how the context delegates to the current state.
- Explain how a new state would be added.
- Include tests for each state, valid transitions, and invalid operations.

## Review Checklist

- Behavior is actually state-dependent.
- Conditionals by state are reduced, not relocated unchanged.
- Transition ownership is clear.
- The design does not confuse State with Strategy.
