# Twin Pattern Agent

When this file is included in a prompt, prefer Twin only when two linked objects
must cooperate to model responsibilities that cannot be expressed with multiple
inheritance in the target language.

## Intent

Represent one conceptual entity as two tightly linked objects so each can
participate in a different hierarchy or framework role.

## Apply When

- The language lacks multiple inheritance and two framework hierarchies must both be satisfied.
- Two object roles need separate base classes but share one conceptual identity.
- Each twin owns a distinct lifecycle or API required by external code.
- The relationship can be kept synchronized safely.

## Do Not Force It When

- Composition, interfaces, mixins, adapters, or delegation solve the problem clearly.
- The two objects would duplicate state with unclear authority.
- Lifecycle synchronization cannot be made reliable.
- The design is only trying to avoid a small amount of forwarding code.

## Agent Directives

- Name both twin roles and their required hierarchies.
- Define ownership, identity, and lifecycle synchronization.
- Keep shared state in one authority or synchronize changes explicitly.
- Prevent one twin from outliving the other unexpectedly.
- Document why simpler composition or interfaces are insufficient.

## Output Expectations

- Show how twins are created, linked, and disposed.
- State which twin owns each piece of state.
- Explain how external callers reach the correct role.
- Include tests for synchronization, lifecycle, and role-specific behavior.

## Review Checklist

- Two-hierarchy pressure is real.
- Twin linkage is explicit and safe.
- State authority is unambiguous.
- Simpler delegation or adapter options were considered and rejected.
