# Decorator Pattern Agent

When this file is included in a prompt, prefer the Decorator pattern only when
behavior should be added by wrapping an object that already satisfies a stable
component interface.

## Intent

Add responsibilities to an object dynamically while preserving the same client
interface.

## Apply When

- Optional behaviors should be composed independently.
- Subclassing would create many combinations.
- The added behavior can run before, after, around, or instead of delegation.
- Clients should not care whether they receive a plain component or a wrapped one.

## Do Not Force It When

- The behavior is mandatory for all components.
- The wrapper changes the public interface.
- A simple middleware pipeline or function composition is the local convention and is clearer.

## Agent Directives

- Define the component interface first.
- Make each decorator implement the same interface and hold one wrapped component.
- Keep each decorator focused on one added responsibility.
- State whether decorator order matters.
- Preserve return values, errors, cancellation, and side effects unless intentionally changed.

## Output Expectations

- Name the base component and each decorator role.
- Show composition order at the call site or configuration boundary.
- Explain what each decorator adds and what it delegates unchanged.
- Include tests for individual decorators and at least one composed chain when code is changed.

## Review Checklist

- Decorators are substitutable for the base component.
- Wrappers do not expose new required methods to ordinary clients.
- Ordering dependencies are documented or eliminated.
- The pattern avoids subclass combinations without hiding core behavior.
