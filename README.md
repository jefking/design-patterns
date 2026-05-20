# design-patterns

Prompt-ready `AGENTS.md` guides for the design patterns listed in the
[Wikipedia software design pattern examples](https://en.wikipedia.org/wiki/Software_design_pattern#Examples).

Each guide is original prompt-control guidance. It is meant to be included in
LLM or coding-agent prompts when you want the agent to bias a solution toward a
specific pattern while still checking whether that pattern actually fits.
Every guide uses the same agent-facing structure: intent, fit checks, anti-fit
checks, implementation directives, output expectations, and review checklist.

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
- [Dependency Injection](creational/dependency-injection/AGENTS.md)
- [Lazy Initialization](creational/lazy-initialization/AGENTS.md)
- [Multiton](creational/multiton/AGENTS.md)
- [Object Pool](creational/object-pool/AGENTS.md)
- [Prototype](creational/prototype/AGENTS.md)
- [Resource Acquisition Is Initialization](creational/resource-acquisition-is-initialization/AGENTS.md)
- [Singleton](creational/singleton/AGENTS.md)

### Structural

- [Adapter](structural/adapter/AGENTS.md)
- [Bridge](structural/bridge/AGENTS.md)
- [Composite](structural/composite/AGENTS.md)
- [Decorator](structural/decorator/AGENTS.md)
- [Delegation](structural/delegation/AGENTS.md)
- [Extension Object](structural/extension-object/AGENTS.md)
- [Facade](structural/facade/AGENTS.md)
- [Flyweight](structural/flyweight/AGENTS.md)
- [Front Controller](structural/front-controller/AGENTS.md)
- [Marker](structural/marker/AGENTS.md)
- [Module](structural/module/AGENTS.md)
- [Proxy](structural/proxy/AGENTS.md)
- [Twin](structural/twin/AGENTS.md)

### Behavioral

- [Blackboard](behavioral/blackboard/AGENTS.md)
- [Chain of Responsibility](behavioral/chain-of-responsibility/AGENTS.md)
- [Command](behavioral/command/AGENTS.md)
- [Fluent Interface](behavioral/fluent-interface/AGENTS.md)
- [Interpreter](behavioral/interpreter/AGENTS.md)
- [Iterator](behavioral/iterator/AGENTS.md)
- [Mediator](behavioral/mediator/AGENTS.md)
- [Memento](behavioral/memento/AGENTS.md)
- [Null Object](behavioral/null-object/AGENTS.md)
- [Observer](behavioral/observer/AGENTS.md)
- [Servant](behavioral/servant/AGENTS.md)
- [Specification](behavioral/specification/AGENTS.md)
- [State](behavioral/state/AGENTS.md)
- [Strategy](behavioral/strategy/AGENTS.md)
- [Template Method](behavioral/template-method/AGENTS.md)
- [Visitor](behavioral/visitor/AGENTS.md)

### Concurrency

- [Active Object](concurrency/active-object/AGENTS.md)
- [Balking](concurrency/balking/AGENTS.md)
- [Binding Properties](concurrency/binding-properties/AGENTS.md)
- [Compute Kernel](concurrency/compute-kernel/AGENTS.md)
- [Double-Checked Locking](concurrency/double-checked-locking/AGENTS.md)
- [Event-Based Asynchronous](concurrency/event-based-asynchronous/AGENTS.md)
- [Guarded Suspension](concurrency/guarded-suspension/AGENTS.md)
- [Join](concurrency/join/AGENTS.md)
- [Lock](concurrency/lock/AGENTS.md)
- [Messaging Design Pattern](concurrency/messaging-design-pattern/AGENTS.md)
- [Monitor Object](concurrency/monitor-object/AGENTS.md)
- [Reactor](concurrency/reactor/AGENTS.md)
- [Read-Write Lock](concurrency/read-write-lock/AGENTS.md)
- [Scheduler](concurrency/scheduler/AGENTS.md)
- [Service Handler](concurrency/service-handler/AGENTS.md)
- [Thread Pool](concurrency/thread-pool/AGENTS.md)
- [Thread-Specific Storage](concurrency/thread-specific-storage/AGENTS.md)
- [Safe Concurrency with Exclusive Ownership](concurrency/safe-concurrency-with-exclusive-ownership/AGENTS.md)
- [CPU Atomic Operation](concurrency/cpu-atomic-operation/AGENTS.md)
