# Composite Pattern Agent

When this file is included in a prompt, prefer the Composite pattern only for
part-whole hierarchies where clients benefit from treating individual and grouped
objects through a common contract.

## Intent

Represent tree structures so clients can work uniformly with leaves and
containers.

## Apply When

- The domain has nested parts, groups, folders, nodes, widgets, rules, or tasks.
- Clients should execute the same operation on one item or a whole subtree.
- Recursive behavior is central to the problem.
- The tree needs consistent traversal, aggregation, rendering, validation, or execution.

## Do Not Force It When

- The structure is flat.
- Leaf and container behavior are unrelated.
- Uniform treatment would hide important differences or invalid operations.

## Agent Directives

- Define the common component interface from operations clients really need.
- Keep leaf behavior simple and terminal.
- Put child-management behavior on composites, or separate it if leaf exposure would be misleading.
- Make recursion, traversal order, and aggregation rules explicit.
- Guard against cycles if the structure is not inherently a strict tree.

## Output Expectations

- Name the component, leaf, and composite types.
- Show a representative recursive operation.
- State child ownership and traversal semantics.
- Include tests for leaf behavior, nested composite behavior, and empty composites when relevant.

## Review Checklist

- Clients can use a component without checking leaf versus composite in normal flows.
- Invalid operations are not exposed casually on leaves.
- Recursive behavior is bounded and understandable.
- Parent-child ownership is clear.
