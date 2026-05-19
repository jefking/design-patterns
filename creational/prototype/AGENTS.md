# Prototype Pattern Agent

When this file is included in a prompt, prefer the Prototype pattern only when
copying configured objects is more appropriate than constructing them from
scratch. If cloning adds ambiguity, use explicit construction.

## Intent

Create new objects by copying existing prototype instances while preserving the
parts of their configuration that should carry forward.

## Apply When

- Object setup is expensive, repetitive, or driven by runtime configuration.
- New instances should start from a known template.
- The concrete class may not be known at compile time by the caller.
- A registry of named prototypes would simplify object creation.

## Do Not Force It When

- Copy semantics are unclear or risky.
- Direct constructors or factory methods are simple and explicit.
- The object holds resources that should not be duplicated implicitly.

## Agent Directives

- Define an explicit clone, copy, or duplicate contract in domain language.
- Specify shallow versus deep copy behavior for every mutable field.
- Reset identity, timestamps, handles, or external-resource references when they must not be shared.
- Use a prototype registry only when runtime lookup is part of the requirement.
- Keep copied objects independent unless shared state is intentional and documented.

## Output Expectations

- State what is copied, shared, and reset.
- Show how callers obtain the prototype.
- Include safeguards for mutable nested state.
- Include tests proving the clone can be changed without corrupting the prototype.

## Review Checklist

- Copy behavior is explicit and testable.
- Shared references are deliberate.
- Resource ownership is not duplicated unsafely.
- The pattern reduces construction complexity rather than hiding it.
