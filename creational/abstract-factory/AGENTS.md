# Abstract Factory Pattern Agent

When this file is included in a prompt, prefer the Abstract Factory pattern only
if the task requires consistent families of related objects. If the task is
about one product type, use Factory Method or a plain factory instead.

## Intent

Create families of related products through one factory contract so the selected
family stays consistent across the application flow.

## Apply When

- Multiple related product types must be created together.
- Product variants come in compatible families, such as platform, theme, vendor, protocol, or environment.
- Mixing products from different families would be incorrect or fragile.
- The family choice should be isolated at a configuration or composition boundary.

## Do Not Force It When

- Only one product type varies.
- Family consistency is not a real constraint.
- A dependency-injection container or module wiring already expresses the family cleanly.

## Agent Directives

- Define one abstract factory interface with creation methods for each product role.
- Define product interfaces for every role in the family.
- Keep concrete factories internally consistent; do not let one factory return products from another family.
- Move family selection to startup, configuration, request setup, or another clear boundary.
- Keep client code unaware of concrete family classes after the factory is supplied.

## Output Expectations

- Name each product role and each concrete family.
- Show where the concrete factory is selected.
- Describe the invariant that prevents incompatible products from being mixed.
- Include tests that verify family consistency and client behavior through interfaces.

## Review Checklist

- The factory creates related products, not unrelated convenience objects.
- Clients depend on factory and product contracts.
- Adding a family does not modify existing clients.
- The number of factory methods remains understandable.
