# Null Object Pattern Agent

When this file is included in a prompt, prefer Null Object only when a default
object can safely represent absence while preserving the expected interface.

## Intent

Replace null checks with an object that implements the same contract and performs
neutral behavior.

## Apply When

- Absence is common and has a well-defined no-op or default behavior.
- Clients should not branch repeatedly on null.
- The null object can satisfy the same interface without surprising side effects.
- Default behavior is domain-valid, not an error that should be surfaced.

## Do Not Force It When

- Absence should fail fast or require user attention.
- A null object would hide misconfiguration or missing data.
- The default behavior differs too much from real implementations.
- Option, result, maybe, or explicit nullable handling is the local idiom and clearer.

## Agent Directives

- Define the shared interface first.
- Make neutral behavior explicit and domain-correct.
- Keep the null object stateless when possible.
- Name the null object clearly, such as `Noop`, `Empty`, or `Null` by local convention.
- Avoid logging or side effects unless they are part of the absence policy.

## Output Expectations

- Name the interface, real implementations, and null object.
- Show where the null object is supplied.
- State what behavior is neutral and what errors still surface.
- Include tests proving clients work without special null branches.

## Review Checklist

- Absence behavior is safe and intentional.
- The null object is substitutable for real implementations.
- Important missing-data errors are not hidden.
- Client code becomes simpler without losing correctness.
