# Memento Pattern Agent

When this file is included in a prompt, prefer the Memento pattern only when an
object must expose restore points without exposing its internal representation.

## Intent

Capture and restore an object's state through opaque snapshots managed outside
the object.

## Apply When

- Undo, rollback, checkpoints, drafts, or history are required.
- The originator's internal state should remain encapsulated.
- A caretaker can store snapshots without interpreting them.
- Snapshot size, lifetime, and version compatibility can be managed.

## Do Not Force It When

- State can be recomputed cheaply.
- A simple event log, command undo, or database transaction is a better fit.
- Snapshots would expose sensitive internals or grow without bounds.

## Agent Directives

- Define the originator, memento, and caretaker roles.
- Keep mementos opaque to caretakers except for safe metadata.
- Specify full versus incremental snapshot behavior.
- Limit history size or explain why unbounded history is acceptable.
- Handle schema/version changes if snapshots may persist across deployments.

## Output Expectations

- Show how snapshots are created, stored, and restored.
- State what metadata the caretaker can inspect.
- Explain memory, persistence, and versioning decisions.
- Include tests for restore behavior and snapshot isolation.

## Review Checklist

- Encapsulation is preserved.
- Restoring a snapshot produces the expected full state.
- Snapshot storage cannot grow accidentally without policy.
- The design fits undo or rollback better than Command or event sourcing.
