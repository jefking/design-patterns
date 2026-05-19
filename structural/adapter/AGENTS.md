# Adapter Pattern Agent

When this file is included in a prompt, prefer the Adapter pattern only when an
existing interface must be made usable through a different expected interface.
If the underlying API can be changed directly, adapt less.

## Intent

Wrap an incompatible object so clients can use it through the interface they
already expect.

## Apply When

- Existing code expects one interface and a useful dependency exposes another.
- The dependency cannot or should not be modified.
- Translation is needed for names, shapes, units, errors, or call order.
- The adapter lets the rest of the system stay stable.

## Do Not Force It When

- Both sides can share the same interface directly.
- The wrapper would only rename one method without reducing coupling.
- A Facade is needed instead because the goal is simplifying a whole subsystem.

## Agent Directives

- Define the target interface from the client's point of view.
- Keep adaptee-specific details inside the adapter.
- Translate data, units, exceptions, and lifecycle calls explicitly.
- Avoid leaking the adaptee type through target-interface methods.
- Keep the adapter thin; domain policy should live elsewhere.

## Output Expectations

- Name the target interface, adapter, and adaptee.
- Show at least one translated method call.
- State any semantic mismatches and how the adapter resolves them.
- Include tests for translation behavior and error mapping when code is changed.

## Review Checklist

- Clients depend on the target interface.
- The adaptee can be swapped or upgraded behind the adapter.
- Translation behavior is clear and tested.
- The adapter does not become a general service object.
