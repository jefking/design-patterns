# Binding Properties Pattern Agent

When this file is included in a prompt, prefer Binding Properties only when
multiple observable properties must remain synchronized through change
notifications.

## Intent

Bind properties so a change in one object updates or constrains related
properties elsewhere.

## Apply When

- UI, configuration, model, or view-model state must stay synchronized.
- Change propagation rules are clear and bounded.
- Updates need notification, transformation, validation, or conflict handling.
- The framework does not already provide a safer binding mechanism.

## Do Not Force It When

- One explicit assignment is clearer.
- Bindings can form cycles without a policy.
- Update order or conflicts are ambiguous.
- Existing reactive or data-binding tools fit the codebase better.

## Agent Directives

- Define source, target, direction, and transformation for each binding.
- Detect or prevent cycles.
- Specify synchronous versus asynchronous propagation.
- Handle validation failures and rollback behavior.
- Dispose bindings to avoid leaks.

## Output Expectations

- Name bound properties and propagation direction.
- Show setup and teardown of a binding.
- State cycle, conflict, and validation behavior.
- Include tests for propagation, transformation, invalid updates, and disposal.

## Review Checklist

- Bindings keep state consistent without hidden loops.
- Update order is deterministic enough for callers.
- Binding lifecycle is explicit.
- Framework-native binding was considered first.
