# design-patterns

Prompt-ready `AGENTS.md` guides for the design patterns listed in the
[Refactoring.Guru design patterns catalog](https://refactoring.guru/design-patterns/catalog).

Each guide is original prompt-control guidance. It is meant to be included in
LLM or coding-agent prompts when you want the agent to bias a solution toward a
specific pattern while still checking whether that pattern actually fits.

## Usage

Include the relevant `AGENTS.md` in a prompt, then ask the agent to follow it as
the governing design constraint for the task. The guides intentionally include
"do not force it" sections so the agent can reject an overfit pattern and choose
simpler code when appropriate.

Example:

```text
Use structural/decorator/AGENTS.md as the design-pattern instruction.
Refactor the notification pipeline so optional logging and retry behavior can be
composed without changing the core sender.
```

## Catalog

### Creational

- [Factory Method](creational/factory-method/AGENTS.md)
- [Abstract Factory](creational/abstract-factory/AGENTS.md)
- [Builder](creational/builder/AGENTS.md)
- [Prototype](creational/prototype/AGENTS.md)
- [Singleton](creational/singleton/AGENTS.md)

### Structural

- [Adapter](structural/adapter/AGENTS.md)
- [Bridge](structural/bridge/AGENTS.md)
- [Composite](structural/composite/AGENTS.md)
- [Decorator](structural/decorator/AGENTS.md)
- [Facade](structural/facade/AGENTS.md)
- [Flyweight](structural/flyweight/AGENTS.md)
- [Proxy](structural/proxy/AGENTS.md)

### Behavioral

- [Chain of Responsibility](behavioral/chain-of-responsibility/AGENTS.md)
- [Command](behavioral/command/AGENTS.md)
- [Iterator](behavioral/iterator/AGENTS.md)
- [Mediator](behavioral/mediator/AGENTS.md)
- [Memento](behavioral/memento/AGENTS.md)
- [Observer](behavioral/observer/AGENTS.md)
- [State](behavioral/state/AGENTS.md)
- [Strategy](behavioral/strategy/AGENTS.md)
- [Template Method](behavioral/template-method/AGENTS.md)
- [Visitor](behavioral/visitor/AGENTS.md)
