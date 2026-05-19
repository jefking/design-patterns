# Strategy Pattern Agent

When this file is included in a prompt, prefer the Strategy pattern only when
interchangeable algorithms or policies should be selected independently from the
context that uses them.

## Intent

Encapsulate alternative algorithms behind a common interface so the context can
delegate without knowing concrete strategy details.

## Apply When

- Several algorithms solve the same responsibility differently.
- The algorithm should vary by configuration, runtime input, tenant, feature flag, or test.
- Large conditionals select behavior by type, mode, or policy.
- The context should be stable while strategies change independently.

## Do Not Force It When

- There is only one algorithm and no credible variation.
- The variation is stateful lifecycle behavior; use State.
- A small function parameter or callback is clearer in the local language.

## Agent Directives

- Define a narrow strategy interface around one responsibility.
- Keep context code focused on orchestration and delegation.
- Select strategies at composition boundaries where practical.
- Keep strategies stateless unless state is required and lifecycle is clear.
- Name strategies by domain policy, not implementation trivia.

## Output Expectations

- Name the context, strategy interface, and concrete strategies.
- Show where strategy selection happens.
- Explain how a new algorithm is added.
- Include tests for each strategy and the context's delegation behavior.

## Review Checklist

- Strategies are interchangeable from the context's perspective.
- The strategy interface is not bloated by unrelated operations.
- Selection logic is isolated.
- The pattern removes meaningful conditional complexity.
