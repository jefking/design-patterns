# Module Pattern Agent

When this file is included in a prompt, prefer Module only when related
functions, types, constants, and state should be grouped behind a clear boundary.

## Intent

Organize related code into one cohesive namespace or unit with an explicit
public surface and hidden implementation details.

## Apply When

- A set of operations and data belong to the same subsystem or domain concept.
- The language supports modules, packages, namespaces, closures, or similar grouping.
- Internal helpers or state should not be exposed broadly.
- The module can offer a smaller public API than its implementation surface.

## Do Not Force It When

- The grouping is arbitrary or purely cosmetic.
- A class, service, or package already provides the right boundary.
- Shared mutable module state would make behavior hard to test.
- The module would become a catch-all utility namespace.

## Agent Directives

- Define the module's public API before adding internals.
- Keep private helpers private by language convention or tooling.
- Avoid unrelated exports.
- Treat module-level mutable state as a lifecycle decision, not a default.
- Match existing package, namespace, and file layout conventions.

## Output Expectations

- Name the module boundary and public exports.
- Identify hidden helpers or private state.
- Explain how clients should import or depend on the module.
- Include tests at the public API boundary when code is changed.

## Review Checklist

- Public exports are cohesive and minimal.
- Internals remain replaceable.
- Module state does not create hidden coupling.
- The module fits local organization rules.
