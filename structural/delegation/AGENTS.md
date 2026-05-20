# Delegation Pattern Agent

When this file is included in a prompt, prefer Delegation only when one object
should hand a focused responsibility to another object instead of inheriting or
duplicating behavior.

## Intent

Extend or vary behavior by forwarding work to a delegate object through a clear
collaboration contract.

## Apply When

- Composition is preferable to subclassing for a responsibility.
- The delegated behavior should vary independently from the delegating object.
- Multiple classes need the same helper behavior without sharing a base class.
- The delegate can own a cohesive policy, operation, or capability.

## Do Not Force It When

- A direct method on the object is simpler and cohesive.
- The delegate would only mirror every method without adding separation.
- Ownership and error handling across delegate calls would be unclear.
- Strategy, Decorator, or Proxy names the relationship more precisely.

## Agent Directives

- Name the delegating object and delegate responsibility.
- Keep the delegate interface narrow and domain-oriented.
- Decide whether the delegate is injected, constructed, or selected at runtime.
- Preserve errors, cancellation, transactions, and context across delegation.
- Avoid chains of tiny delegates that obscure simple logic.

## Output Expectations

- Show the call that delegates work.
- Explain what coupling or duplication delegation removes.
- State delegate lifecycle and replacement behavior.
- Include tests for delegated behavior and delegating-object integration.

## Review Checklist

- Delegation improves cohesion or variability.
- The delegate owns a meaningful responsibility.
- The delegating object does not leak delegate internals unnecessarily.
- Composition remains easier to follow than inheritance would be.
