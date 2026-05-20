# Lazy Initialization Pattern Agent

When this file is included in a prompt, prefer Lazy Initialization only when
delaying creation or computation has a real startup, cost, or ordering benefit.

## Intent

Defer creation of an object, resource, or computed value until the first time it
is needed.

## Apply When

- Initialization is expensive and the value may not be used.
- Startup time or memory use matters.
- A resource depends on configuration or context that is not available earlier.
- Cached computed values need clear invalidation or refresh behavior.

## Do Not Force It When

- The value is cheap or always needed.
- Delayed initialization would move failures to surprising points in the flow.
- The code would need unsafe double-checked locking or unclear concurrency rules.
- Resource teardown cannot be defined after delayed creation.

## Agent Directives

- Identify the trigger that initializes the value.
- Define failure behavior: retry, cache the failure, or surface each failure.
- Make initialization thread-safe when the value can be accessed concurrently.
- Keep lazy state private behind a small access method.
- Define reset, refresh, and cleanup behavior when the value owns resources.

## Output Expectations

- Name the lazy value and first-use path.
- State concurrency guarantees.
- Explain initialization failure and retry behavior.
- Include tests for uninitialized, initialized, repeated access, and failure cases.

## Review Checklist

- Initialization happens at most when intended.
- Callers see predictable errors and lifecycle behavior.
- Lazy state does not leak partially initialized values.
- The added indirection is justified by cost or ordering.
