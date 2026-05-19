# Singleton Pattern Agent

When this file is included in a prompt, treat Singleton as a constrained option,
not a default. Prefer dependency injection unless there is a real process-wide
instance requirement.

## Intent

Ensure one accessible instance of a component when the domain or runtime truly
requires one shared coordinator.

## Apply When

- The instance represents a unique process-wide resource or coordinator.
- Multiple instances would break correctness, not merely convenience.
- Lifetime, concurrency, and test reset behavior can be defined clearly.
- The language or framework does not already provide an appropriate lifecycle container.

## Do Not Force It When

- The goal is only to avoid passing dependencies.
- Tests need isolated instances and there is no reset or injection seam.
- The object holds request, user, tenant, or transaction-specific state.
- A module-level function, dependency-injection binding, or application service is clearer.

## Agent Directives

- Document why one instance is required.
- Keep mutable state minimal and protected.
- Make initialization thread-safe if the runtime can initialize concurrently.
- Provide a test strategy: reset hook, injected interface, or isolated container.
- Keep callers typed against an interface when practical.

## Output Expectations

- Name the singleton responsibility and lifecycle.
- Show initialization, access, and teardown behavior.
- Explain concurrency guarantees.
- Include tests for identity, initialization, and any reset path used in tests.

## Review Checklist

- Singleton is justified by correctness, not convenience.
- Hidden global state is minimized.
- Tests can run independently.
- The design remains replaceable for integration boundaries.
