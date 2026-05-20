# Dependency Injection Pattern Agent

When this file is included in a prompt, prefer Dependency Injection only when a
component should receive collaborators from outside instead of constructing or
locating them internally.

## Intent

Supply required dependencies through explicit inputs so construction, lifetime,
and replacement are controlled at a composition boundary.

## Apply When

- A class or function needs collaborators that may vary by environment, test, tenant, or feature.
- The dependency has a meaningful lifecycle, configuration, or external resource behind it.
- Callers should depend on a contract rather than a concrete implementation.
- Tests need to supply fakes, stubs, or controlled implementations.

## Do Not Force It When

- The value is plain data or a cheap object naturally created by the component.
- A function parameter is clearer than introducing a dependency object.
- A dependency-injection container would hide wiring more than it helps.
- The pattern would become a service locator or global registry in disguise.

## Agent Directives

- Define dependency contracts from the consumer's needs.
- Prefer constructor or initializer injection for required dependencies.
- Use method or parameter injection for request-scoped or operation-specific collaborators.
- Keep container access at composition roots; do not reach into containers from domain logic.
- State dependency lifetime, ownership, and teardown behavior when resources are involved.

## Output Expectations

- Name the consumer, dependency contracts, concrete implementations, and composition point.
- Show how required dependencies are supplied.
- Explain replacement behavior for tests or alternate environments.
- Include tests that verify behavior through injected dependencies when code is changed.

## Review Checklist

- Dependencies are explicit and required ones cannot be forgotten silently.
- Consumer code depends on narrow contracts, not broad containers.
- Lifecycle and cleanup are owned at the correct boundary.
- Injection improves substitutability without scattering wiring logic.
