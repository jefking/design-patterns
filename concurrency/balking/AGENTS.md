# Balking Pattern Agent

When this file is included in a prompt, prefer Balking only when an operation
should do nothing or fail immediately unless the object is in the right state.

## Intent

Check state before acting and abandon the operation when preconditions are not
satisfied.

## Apply When

- Repeated or concurrent calls may arrive while work is already running or unavailable.
- The correct response to the wrong state is skip, no-op, or immediate rejection.
- Waiting would be incorrect or wasteful.
- The state check can be made atomic with the state transition.

## Do Not Force It When

- Callers should wait until the precondition becomes true; use Guarded Suspension.
- Retrying or queuing is required.
- Silent no-op would hide a bug.
- State checks cannot be synchronized safely.

## Agent Directives

- Define allowed states and balk states.
- Make the check-and-transition atomic when concurrency is possible.
- Decide whether balking returns a status, throws, logs, or silently exits.
- Keep skipped work observable if operations are important.
- Avoid long-running work while holding locks unless required.

## Output Expectations

- Show the state guard and operation path.
- State caller-visible behavior when balking occurs.
- Explain concurrency protection.
- Include tests for allowed state, balk state, and concurrent calls.

## Review Checklist

- Balking is the correct semantic response.
- State transitions are race-safe.
- Callers can distinguish skipped work when they need to.
- The operation does not mask failures that should be handled.
