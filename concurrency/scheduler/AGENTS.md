# Scheduler Pattern Agent

When this file is included in a prompt, prefer Scheduler only when execution
order, timing, priority, or concurrency limits must be controlled explicitly.

## Intent

Decide when queued work runs and which worker, thread, task, or time slot should
execute it.

## Apply When

- Work must be ordered by time, priority, fairness, dependency, or capacity.
- Concurrency must be limited or shaped.
- Retries, delays, cron-like timing, or rate limits are part of the requirement.
- Scheduling policy needs tests and observability.

## Do Not Force It When

- The platform executor, event loop, or job queue already supplies the needed policy.
- Immediate direct execution is correct.
- Timing precision or persistence requirements exceed local implementation.
- Scheduling rules are vague or likely to become a full workflow engine.

## Agent Directives

- Define job shape, queue, policy, workers, and clock source.
- Make priority, fairness, delay, retry, and cancellation behavior explicit.
- Use injectable clocks for deterministic tests.
- Bound queues or define overload behavior.
- Record scheduling decisions and failures for observability when operationally relevant.

## Output Expectations

- Name scheduled work and scheduling policy.
- Show enqueue, dispatch, cancel, and retry flows.
- State persistence, clock, and overload behavior.
- Include tests for ordering, delay, priority, cancellation, and retry.

## Review Checklist

- Scheduling policy is explicit and needed.
- Time-dependent behavior is testable.
- Queue growth and worker limits are controlled.
- Existing scheduling tools were considered.
