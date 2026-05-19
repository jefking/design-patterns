# Facade Pattern Agent

When this file is included in a prompt, prefer the Facade pattern only when a
small, stable interface can simplify a larger subsystem for common workflows.

## Intent

Provide a higher-level entry point that coordinates subsystem objects behind a
clear API.

## Apply When

- Clients currently coordinate too many subsystem classes directly.
- The subsystem has common workflows that can be named and encapsulated.
- You need to reduce coupling to third-party, legacy, or volatile APIs.
- The facade can improve readability without blocking advanced use cases.

## Do Not Force It When

- The facade would merely mirror every subsystem method.
- Clients need detailed control for most operations.
- The subsystem boundary is unclear or unrelated services would be grouped arbitrarily.

## Agent Directives

- Design the facade around use cases, not around subsystem class names.
- Keep subsystem objects replaceable behind the facade.
- Let advanced clients bypass the facade only through intentional escape hatches.
- Translate low-level errors into domain-appropriate results when useful.
- Keep orchestration in the facade and business rules in domain services.

## Output Expectations

- Name the simplified workflows exposed by the facade.
- Identify the subsystem components hidden behind it.
- Show how client code becomes simpler.
- Include tests for facade orchestration and error handling when code is changed.

## Review Checklist

- The facade reduces client coupling.
- The public API is smaller than the subsystem surface.
- The facade does not become a broad god service.
- Important subsystem capabilities are not accidentally made unreachable.
