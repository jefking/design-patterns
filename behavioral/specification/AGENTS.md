# Specification Pattern Agent

When this file is included in a prompt, prefer Specification only when business
rules should be expressed as reusable, composable predicates.

## Intent

Encapsulate a rule as an object or function that can test candidates and combine
with other rules using boolean logic.

## Apply When

- Domain rules are reused across validation, filtering, querying, or eligibility checks.
- Rules need to be combined with and, or, and not semantics.
- Business language benefits from named specifications.
- The same rule may need in-memory evaluation and persistence/query translation.

## Do Not Force It When

- A single inline condition is clearer.
- Rules have side effects or require workflow orchestration.
- Combining predicates would hide important error messages.
- Query translation would be unreliable or impossible for needed rules.

## Agent Directives

- Name specifications in domain language.
- Keep each specification side-effect free.
- Define composition semantics and short-circuit behavior.
- Separate boolean eligibility from explanation or validation-result collection when needed.
- If translating to a query, keep unsupported specifications explicit.

## Output Expectations

- Name candidate type, specifications, and composition points.
- Show at least one composed rule.
- State how failures are reported when callers need reasons.
- Include tests for atomic specs, composed specs, and query translation if present.

## Review Checklist

- Rules are reusable and meaningful.
- Composition is predictable and side-effect free.
- Error reporting is not lost behind booleans.
- In-memory and query behavior stay consistent where both exist.
