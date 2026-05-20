# Thread-Specific Storage Pattern Agent

When this file is included in a prompt, prefer Thread-Specific Storage only when
each thread needs its own instance of otherwise shared-looking state.

## Intent

Provide data that is global in access shape but isolated per thread of
execution.

## Apply When

- A non-thread-safe object must be reused within one thread.
- Per-thread context, caches, formatters, or buffers reduce contention safely.
- Thread lifetime and cleanup are predictable.
- The codebase already uses thread-local or task-local context idiomatically.

## Do Not Force It When

- Async tasks can hop threads and need task-local or request-local storage instead.
- Hidden context would make behavior hard to test.
- Values may leak across requests on reused worker threads.
- Passing explicit context is clearer.

## Agent Directives

- Choose thread-local, task-local, coroutine-local, or request context based on runtime behavior.
- Define initialization and cleanup for each thread's value.
- Avoid storing user, tenant, or security context without strict clearing.
- Keep access points narrow and documented.
- Provide test helpers to set and clear storage.

## Output Expectations

- Name stored value and isolation boundary.
- Show get, set, initialization, and cleanup.
- State behavior under async execution or worker reuse.
- Include tests for isolation, cleanup, and missing context behavior.

## Review Checklist

- Thread-specific state matches runtime execution model.
- Values cannot leak between requests or tests.
- Explicit context passing was considered.
- Cleanup is reliable.
