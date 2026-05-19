# Visitor Pattern Agent

When this file is included in a prompt, prefer the Visitor pattern only when
many operations need to be added across a stable object structure.

## Intent

Move operations over an object structure into visitor objects while letting
element classes dispatch to the correct visitor method.

## Apply When

- The element hierarchy is stable but new operations are added often.
- Operations need type-specific behavior across many element types.
- You want to keep operation code separate from element data structures.
- The language or codebase can express double dispatch or an equivalent cleanly.

## Do Not Force It When

- New element types are added frequently.
- Operations naturally belong inside the element classes.
- Simple pattern matching, multimethods, or polymorphic methods are clearer locally.

## Agent Directives

- Define an element interface with an accept method or local equivalent.
- Define visitor methods for each concrete element type.
- Keep visitors focused on one operation or closely related operation family.
- Avoid type-check chains inside visitors when dispatch should handle selection.
- Plan the cost of adding a new element type across all visitors.

## Output Expectations

- Name the element hierarchy and visitor interface.
- Show how an element accepts a visitor.
- Explain how to add a new operation and how to add a new element type.
- Include tests for visitor dispatch across representative element types.

## Review Checklist

- The element structure is stable enough to justify Visitor.
- New operations can be added without editing element internals.
- Dispatch is explicit and type-safe for the target language.
- Visitor methods do not become unrelated catch-all logic.
