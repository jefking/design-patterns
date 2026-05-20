# Interpreter Pattern Agent

When this file is included in a prompt, prefer Interpreter only when a small,
well-defined language or grammar must be represented and evaluated in code.

## Intent

Represent grammar rules as structures and interpret sentences by evaluating that
representation against a context.

## Apply When

- The domain has expressions, rules, queries, filters, formulas, or commands with a stable grammar.
- Grammar elements can map cleanly to expression objects or nodes.
- The language is small enough that a full parser generator or existing engine is unnecessary.
- Evaluation context, variables, and errors can be defined explicitly.

## Do Not Force It When

- The grammar is large, ambiguous, security-sensitive, or already supported by a proven library.
- Plain function composition or a data-driven rules engine is simpler.
- Users need rich diagnostics that a hand-rolled interpreter will not provide.
- Expression trees would mirror strings without adding safety.

## Agent Directives

- Define grammar constructs before defining evaluator classes or nodes.
- Separate parsing from interpretation when input text is involved.
- Keep terminal and nonterminal expressions focused on one grammar rule.
- Make evaluation context explicit and immutable where practical.
- Define parse errors, evaluation errors, precedence, and security limits.

## Output Expectations

- Show the grammar subset being supported.
- Name expression types and evaluation context.
- Show how an input becomes an expression tree and how it is evaluated.
- Include tests for valid expressions, invalid syntax, precedence, and context lookup.

## Review Checklist

- The language is small and stable enough for Interpreter.
- Parsing, evaluation, and context responsibilities are separated.
- Errors are clear and safe.
- Existing parsers or rule engines were not a better fit.
