# Resource Acquisition Is Initialization Pattern Agent

When this file is included in a prompt, prefer Resource Acquisition Is
Initialization only when resource lifetime should be bound to object or scope
lifetime.

## Intent

Acquire a resource during initialization and release it automatically when the
owning object or scope ends.

## Apply When

- A resource must be released reliably, such as files, locks, sockets, handles, or transactions.
- The language supports deterministic destruction, defer, context managers, using blocks, or similar scope cleanup.
- Ownership can be expressed as one clear object or scope.
- Exceptions or early returns must not skip cleanup.

## Do Not Force It When

- The runtime cannot guarantee timely cleanup and no explicit close path exists.
- Resource ownership is shared or transferred in complex ways.
- A managed framework lifecycle already owns the resource safely.
- Initialization failure would leave partially acquired resources ambiguous.

## Agent Directives

- Acquire resources in the same construct that owns cleanup.
- Release resources in deterministic teardown paths.
- Define move, copy, transfer, or shared ownership behavior if the language permits it.
- Make partial-initialization failure clean up already acquired resources.
- Avoid finalizers as the only cleanup mechanism for scarce resources.

## Output Expectations

- Name the resource owner and resource lifetime boundary.
- Show acquisition, normal release, and failure release paths.
- State ownership transfer rules.
- Include tests or examples proving cleanup on success and error paths.

## Review Checklist

- Cleanup is deterministic for the target language.
- Resource ownership is clear and not accidentally copied.
- Early returns and exceptions cannot leak the resource.
- The pattern fits local lifecycle conventions.
