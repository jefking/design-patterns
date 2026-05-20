# Object Pool Pattern Agent

When this file is included in a prompt, prefer Object Pool only when acquiring
or creating objects is expensive and reuse can be made safe.

## Intent

Reuse a managed set of objects or resources instead of repeatedly creating and
destroying them.

## Apply When

- Objects wrap scarce, expensive, or rate-limited resources.
- Creation and teardown cost is significant under expected load.
- Borrowed objects can be reset to a safe state before reuse.
- The pool can enforce capacity, waiting, timeout, and disposal policies.

## Do Not Force It When

- Objects are cheap to allocate or managed well by the runtime.
- Reuse risks stale state, data leaks, or broken ownership.
- The pool would hide resource exhaustion instead of handling it.
- Existing platform pools already solve the problem.

## Agent Directives

- Define acquire, release, reset, validation, and disposal behavior.
- Make ownership rules explicit: borrowed objects must be returned once.
- Protect the pool against leaks, double release, and use-after-release when practical.
- Set capacity, timeout, and backpressure behavior deliberately.
- Instrument or expose pool health when operationally useful.

## Output Expectations

- Name the pooled object, pool, and borrower responsibilities.
- Show acquire/release flow, including failure paths.
- State reset and validation behavior before reuse.
- Include tests for reuse, exhaustion, release, and stale-state prevention.

## Review Checklist

- Reuse is safe after reset.
- Pool capacity and waiting behavior are defined.
- Resource leaks and double releases are handled or made visible.
- The pool is justified by cost, scarcity, or load.
