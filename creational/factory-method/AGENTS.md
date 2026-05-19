# Factory Method Pattern Agent

When this file is included in a prompt, prefer the Factory Method pattern only
if the problem matches the fit checks below. If it does not fit, state the
mismatch briefly and use simpler construction.

## Intent

Create products through a creator operation so clients depend on a product
contract instead of concrete product classes.

## Apply When

- Several product variants share a stable interface.
- The code that chooses a concrete product belongs near a creator, subclass, plugin, or framework hook.
- New product types should be added without changing ordinary client code.
- Construction needs a named extension point, not just a direct constructor call.

## Do Not Force It When

- There is only one concrete product and no credible variation.
- A small factory function at the composition boundary is enough.
- The design would add inheritance only to hide a trivial constructor.

## Agent Directives

- Define the product interface first, using names from the domain.
- Put concrete-product selection in the creator method or its overrides.
- Keep clients typed against the product interface wherever practical.
- Keep concrete product references at setup, registration, or creator boundaries.
- Make the extension path obvious: adding a product should add a class and a creator decision, not scatter conditionals.

## Output Expectations

- Name the creator, product interface, and concrete products.
- Show where the factory method is invoked.
- Explain how a new product type would be introduced.
- Include focused tests for product selection and shared product behavior when code is changed.

## Review Checklist

- Client code avoids direct dependency on every concrete product.
- The creator has a real reason to own construction.
- Product variants honor the same contract.
- The pattern does not obscure a simpler dependency-injection setup.
