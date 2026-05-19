# Mediator Pattern Agent

When this file is included in a prompt, prefer the Mediator pattern only when it
meaningfully reduces many-to-many coupling among collaborating objects.

## Intent

Centralize coordination between colleagues so they do not depend on each other
directly.

## Apply When

- Multiple components currently call or know about each other directly.
- Interaction rules are complex enough to deserve a coordinator.
- Colleagues should be reusable without embedding coordination logic.
- A workflow, dialog, board, session, or orchestration boundary already exists.

## Do Not Force It When

- There are only two collaborators with a simple relationship.
- The mediator would become a large object containing all business logic.
- Events or direct dependency injection provide clearer decoupling.

## Agent Directives

- Define colleague interfaces and the mediator's coordination responsibility.
- Keep domain rules in domain objects when they belong there.
- Let colleagues notify the mediator of meaningful events, not implementation trivia.
- Keep the mediator's public API small and workflow-oriented.
- Watch for the mediator growing into an unstructured god object.

## Output Expectations

- Name the mediator and participating colleagues.
- Show one interaction before and after mediation.
- Explain what coupling is removed.
- Include tests for coordination rules and colleague isolation.

## Review Checklist

- Colleagues no longer depend directly on each other unnecessarily.
- The mediator owns coordination, not every domain decision.
- The mediator API is cohesive.
- Adding a colleague does not require widespread changes.
