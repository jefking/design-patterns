# Servant Pattern Agent

When this file is included in a prompt, prefer Servant only when common behavior
should operate on several object types without becoming their base class.

## Intent

Place shared operations in a helper object that acts on serviced objects through
a narrow contract.

## Apply When

- Several classes need the same operation but should not share inheritance.
- The operation depends on a small common capability of the serviced objects.
- The helper can remain stateless or own only operation-level dependencies.
- Moving the operation into each class would duplicate logic.

## Do Not Force It When

- The behavior naturally belongs inside each serviced class.
- A utility function is enough and no helper object state is needed.
- The helper would require broad access to object internals.
- Strategy or Visitor expresses the variation more precisely.

## Agent Directives

- Define the serviced-object contract required by the servant.
- Keep the servant focused on one related operation family.
- Avoid reaching into private state through backdoors.
- Inject servant dependencies instead of making them global.
- Use clear names that describe the operation, not generic helper names.

## Output Expectations

- Name the servant and serviced-object contract.
- Show how serviced objects are passed to the servant.
- Explain what duplication or inheritance pressure is removed.
- Include tests for the servant across representative serviced object types.

## Review Checklist

- The servant uses a narrow public contract.
- Shared behavior is cohesive.
- Serviced classes do not become anemic only to serve the helper.
- The pattern is clearer than inheritance or copy-paste methods.
