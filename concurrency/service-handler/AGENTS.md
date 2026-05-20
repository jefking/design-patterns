# Service Handler Pattern Agent

When this file is included in a prompt, prefer Service Handler only when each
client session or request needs a dedicated handler with clear lifecycle.

## Intent

Accept incoming requests and assign each connection, session, or request to a
handler responsible for its protocol interaction.

## Apply When

- Each client interaction has stateful protocol or session behavior.
- A handler can own request parsing, response writing, and session cleanup.
- The acceptor or front end should stay separate from per-client work.
- Thread, task, or actor allocation per handler is acceptable or bounded.

## Do Not Force It When

- Stateless request handlers in the framework already fit.
- One handler per client would exhaust resources under load.
- Event-loop or reactor handling is required for scale.
- Session state can be externalized more simply.

## Agent Directives

- Separate acceptor/listener concerns from service-handler concerns.
- Define handler lifecycle: create, serve, error, close.
- Bound concurrency or use a worker pool when needed.
- Make protocol parsing and response behavior testable without real sockets.
- Ensure cleanup runs for disconnects, errors, and shutdown.

## Output Expectations

- Name acceptor, service handler, and session/request state.
- Show how handlers are created and closed.
- State concurrency and resource limits.
- Include tests for normal session, parse error, disconnect, and cleanup.

## Review Checklist

- Per-client handler ownership is justified.
- Resource usage is bounded.
- Cleanup is reliable.
- The handler is not overloaded with global server policy.
