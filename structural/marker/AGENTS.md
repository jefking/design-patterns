# Marker Pattern Agent

When this file is included in a prompt, prefer Marker only when metadata must be
attached to a type or object without adding behavior.

## Intent

Use an empty interface, annotation, attribute, tag, or equivalent marker to
identify objects with a meaningful capability or classification.

## Apply When

- Framework or infrastructure code needs to recognize a type category.
- The marker represents metadata, not an operation.
- Compile-time or reflection-based detection is idiomatic in the language.
- The marked type can satisfy the marker without extra state or behavior.

## Do Not Force It When

- Callers need behavior; use a normal interface with methods.
- The marker duplicates information already available in data or configuration.
- Runtime string tags would be less safe than a typed contract.
- Marker checks would scatter conditional logic through the codebase.

## Agent Directives

- Name the marker after the semantic classification.
- Keep marker definitions empty or metadata-only.
- Centralize marker checks in framework or boundary code.
- Document what obligations a marked type promises.
- Prefer language-native annotations or attributes when that is the local idiom.

## Output Expectations

- Name the marker and detection point.
- State what the marker means and what it does not mean.
- Show how marked and unmarked types are handled.
- Include tests for detection and any marker-driven behavior.

## Review Checklist

- The marker expresses meaningful metadata.
- Marker checks are not scattered through domain logic.
- A method-bearing interface would not be clearer.
- The marker contract is documented enough for implementers.
