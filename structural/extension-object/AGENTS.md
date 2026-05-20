# Extension Object Pattern Agent

When this file is included in a prompt, prefer Extension Object only when a
stable object hierarchy needs optional capabilities without modifying every base
type.

## Intent

Attach optional extension interfaces to objects so clients can discover and use
capabilities without changing the core object hierarchy.

## Apply When

- Core objects are stable or externally owned.
- Capabilities vary by object, plugin, module, or runtime environment.
- Adding methods to the base interface would bloat it or break implementers.
- Clients can handle absent extensions explicitly.

## Do Not Force It When

- The capability belongs on every object in the hierarchy.
- A normal interface, adapter, or composition field is clearer.
- Extension lookup would become stringly typed or hard to validate.
- Missing capability behavior cannot be handled safely.

## Agent Directives

- Define extension contracts as narrow, typed interfaces.
- Provide an explicit extension lookup or registration mechanism.
- Keep extension lifetime tied to the host object or documented separately.
- Make absence of an extension explicit through option/result/null-object behavior.
- Avoid using extensions as a bag for unrelated methods.

## Output Expectations

- Name the host object, extension interface, and lookup mechanism.
- Show how a client checks for and uses an extension.
- State what happens when an extension is unavailable.
- Include tests for present, absent, and incompatible extensions.

## Review Checklist

- The base hierarchy stays stable and cohesive.
- Extension discovery is typed or otherwise safe.
- Optional behavior is handled deliberately.
- Extensions do not bypass core invariants.
