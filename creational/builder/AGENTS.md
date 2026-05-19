# Builder Pattern Agent

When this file is included in a prompt, prefer the Builder pattern only when
construction has meaningful steps, options, validation, or representations. If
the object can be built clearly with a constructor or literal, use that instead.

## Intent

Separate complex construction from the final object so callers can assemble a
valid result step by step without knowing every construction detail.

## Apply When

- Constructors have too many optional or order-sensitive parameters.
- The same construction process can produce different representations.
- Intermediate validation, defaults, or derived values matter.
- The final object should be immutable or hard to construct in an invalid state.

## Do Not Force It When

- The object has only a few obvious fields.
- Named parameters, records, data classes, or object literals are clearer.
- A builder would duplicate the final object's full API without adding safety.

## Agent Directives

- Keep the product's invariants in one place: the builder's final build step or the product constructor.
- Use fluent methods only if they improve readability in the target language.
- Make required fields explicit through constructor parameters, staged builders, or validation.
- Keep builder state private and avoid exposing partially built products.
- Prefer domain verbs for build steps instead of generic setters when the sequence matters.

## Output Expectations

- Identify required and optional construction inputs.
- Show the build step that returns the finished product.
- State validation behavior for missing or incompatible options.
- Include tests for defaults, invalid combinations, and a representative successful build.

## Review Checklist

- The builder prevents or detects invalid products.
- The final product is not accidentally mutable through builder internals.
- The call site is clearer than a long constructor call.
- The builder does not become a dumping ground for unrelated business logic.
