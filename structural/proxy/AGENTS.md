# Proxy Pattern Agent

When this file is included in a prompt, prefer the Proxy pattern only when an
object with the same interface should control access to another object.

## Intent

Stand in for a real subject to add access control, lazy loading, remote access,
caching, logging, rate limiting, or other access behavior while preserving the
subject contract.

## Apply When

- Clients should call the same interface regardless of whether they receive the real subject or proxy.
- Access to the real subject requires coordination, security, lifecycle control, or expensive setup.
- Cross-cutting access behavior belongs at the boundary to the subject.
- The proxy can preserve the real subject's semantics.

## Do Not Force It When

- The interface must be transformed; use Adapter.
- The goal is to simplify many subsystem calls; use Facade.
- The proxy would surprise clients by changing core behavior.

## Agent Directives

- Define or reuse the subject interface.
- Keep the proxy substitutable for the real subject.
- Make lazy initialization, caching, authorization, or remote-call behavior explicit.
- Preserve errors, return values, cancellation, and transaction boundaries unless intentionally changed.
- Avoid mixing unrelated concerns in one proxy.

## Output Expectations

- Name the subject, real subject, and proxy.
- State which access concern the proxy owns.
- Show where the real subject is created or injected.
- Include tests for access behavior and pass-through semantics when code is changed.

## Review Checklist

- Clients can use proxy and real subject interchangeably.
- The proxy does not leak internal access mechanics.
- Added behavior is observable and tested.
- The proxy is not a disguised adapter or facade.
