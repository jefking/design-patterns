# Front Controller Pattern Agent

When this file is included in a prompt, prefer Front Controller only when
requests need a centralized entry point for shared handling before dispatch.

## Intent

Route incoming requests through one controller boundary that owns common
preprocessing, routing, security, and dispatch concerns.

## Apply When

- Many entry points duplicate authentication, authorization, logging, parsing, or error handling.
- Routing and dispatch should be consistent across handlers.
- A web, UI, CLI, or message system has a clear request boundary.
- Cross-cutting request behavior belongs before specific handlers run.

## Do Not Force It When

- The framework already provides an idiomatic routing layer.
- Centralization would create a large controller full of business logic.
- Independent entry points require different lifecycles or protocols.
- Middleware or filters express the shared behavior more clearly.

## Agent Directives

- Keep the front controller focused on request boundary concerns.
- Dispatch to handlers, actions, commands, or use cases for business work.
- Make routing, authentication, validation, and error mapping explicit.
- Preserve request context and cancellation across dispatch.
- Avoid placing handler-specific policy in the front controller.

## Output Expectations

- Name the front controller, request type, dispatch target, and shared concerns.
- Show the request path from entry through handler.
- Explain how new routes or actions are registered.
- Include tests for routing, shared preprocessing, and error handling.

## Review Checklist

- Shared request behavior is centralized without swallowing domain logic.
- Dispatch rules are clear and testable.
- Handlers stay independently understandable.
- The design follows the local framework instead of fighting it.
