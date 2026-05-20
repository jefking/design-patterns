# Double-Checked Locking Pattern Agent

When this file is included in a prompt, treat Double-Checked Locking as a risky
optimization. Prefer language-provided lazy initialization unless evidence shows
manual double checks are necessary and safe.

## Intent

Avoid repeated lock acquisition by checking initialization state before and after
acquiring a lock.

## Apply When

- Lazy initialization is needed and lock overhead is a measured concern.
- The language memory model supports a correct implementation.
- The shared reference can be published safely.
- A simpler built-in primitive is unavailable or unsuitable.

## Do Not Force It When

- Built-in lazy, once, static initialization, or dependency injection is available.
- The language memory model makes the pattern unsafe or hard to verify.
- Initialization can run eagerly without cost.
- Correctness depends on partially initialized objects never being observed.

## Agent Directives

- Verify the target language memory model before implementing.
- Use volatile, atomic, mutex, once, or memory barriers as required by the language.
- Keep initialization side effects idempotent or protected.
- Document why a simpler primitive is not used.
- Add concurrency tests, but do not rely on tests alone to prove memory safety.

## Output Expectations

- Name the protected value and initialization path.
- State the memory-safety mechanism.
- Explain fallback to simpler primitives when available.
- Include tests for single initialization and concurrent access.

## Review Checklist

- Implementation is valid for the language and runtime.
- No partially initialized value can be observed.
- The optimization is justified.
- A safer built-in alternative was checked first.
