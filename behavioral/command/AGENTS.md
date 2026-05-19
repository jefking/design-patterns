# Command Pattern Agent

When this file is included in a prompt, prefer the Command pattern only when
requests need to be represented as objects for execution, scheduling, undo,
logging, retries, permissions, or transport.

## Intent

Encapsulate an action and its inputs as an object so invocation can be decoupled
from the code that performs the work.

## Apply When

- Actions need to be queued, stored, retried, audited, undone, or sent elsewhere.
- The invoker should not know the receiver's concrete API.
- User actions or workflow steps need a common execution contract.
- Permissions, validation, or metadata travel with the action.

## Do Not Force It When

- A direct method call is sufficient.
- The command only wraps one call and will never be stored or composed.
- Capturing receiver state would make undo or retry misleading.

## Agent Directives

- Define a command interface with execution semantics.
- Keep command inputs explicit and serializable when persistence or transport is required.
- Separate invoker, command, and receiver responsibilities.
- Define undo, idempotency, retry, and error behavior only when the use case requires them.
- Avoid putting unrelated workflow orchestration into individual commands.

## Output Expectations

- Name the invoker, command, concrete commands, and receiver.
- Show how commands are created and executed.
- State whether commands support undo, retry, persistence, or audit metadata.
- Include tests for command execution and any undo or retry behavior.

## Review Checklist

- Commands represent meaningful actions.
- The invoker is decoupled from receiver details.
- State captured by commands is correct at execution time.
- Error and repeat-execution behavior is defined.
