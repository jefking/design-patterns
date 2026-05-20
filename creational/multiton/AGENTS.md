# Multiton Pattern Agent

When this file is included in a prompt, prefer Multiton only when there must be
one shared instance per key or name, and those keys are part of the domain.

## Intent

Provide controlled access to a limited set of named instances while preventing
accidental duplicate instances for the same key.

## Apply When

- The domain has a known set of named coordinators, resources, or contexts.
- Each key must map to one shared instance for correctness.
- Instance creation needs central validation, caching, or lifecycle management.
- Callers should not construct keyed instances directly.

## Do Not Force It When

- Keys are unbounded and cache growth would be uncontrolled.
- Duplicate instances are harmless.
- Dependency injection or an ordinary registry gives clearer ownership.
- Hidden global mutable state would make tests or tenants interfere.

## Agent Directives

- Define the key type and valid key set clearly.
- Keep the instance registry private.
- Make lookup and creation thread-safe when concurrent access is possible.
- Define eviction, reset, and teardown if keys are dynamic.
- Avoid placing unrelated global services behind the same multiton.

## Output Expectations

- Name the keyed instance type, key space, and access point.
- Show how callers obtain an instance.
- State lifecycle, eviction, and test-reset behavior.
- Include tests for same-key identity, different-key separation, and invalid keys.

## Review Checklist

- One-instance-per-key is a correctness requirement, not convenience.
- Registry growth is bounded or deliberately managed.
- Key validation is explicit.
- Tests can isolate or reset shared instances.
