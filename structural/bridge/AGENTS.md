# Bridge Pattern Agent

When this file is included in a prompt, prefer the Bridge pattern only when two
dimensions vary independently. If there is only one axis of variation, use a
simpler interface or composition.

## Intent

Separate an abstraction from its implementation so each side can evolve without
creating a subclass combination for every variant.

## Apply When

- There are independent abstraction variants and implementation variants.
- Subclass combinations are multiplying or likely to multiply.
- Runtime selection of an implementation is useful.
- High-level operations should not depend on low-level implementation details.

## Do Not Force It When

- A single interface and one implementation is enough.
- The abstraction is just a pass-through wrapper.
- The implementation axis is unlikely to vary.

## Agent Directives

- Name the high-level abstraction and the implementation interface separately.
- Put user-facing behavior in the abstraction.
- Put platform, backend, driver, renderer, or transport details behind the implementation interface.
- Use composition from abstraction to implementation.
- Keep both hierarchies independently extensible.

## Output Expectations

- Identify the two axes of variation.
- Show how the abstraction delegates to the implementation.
- Explain how to add one new abstraction without adding new implementations, and the reverse.
- Include tests that pair at least two abstractions or implementations when code is changed.

## Review Checklist

- The two axes are real and independent.
- The abstraction is not coupled to concrete implementation classes.
- Adding combinations does not require subclass explosion.
- Delegation boundaries are clear and not excessively chatty.
