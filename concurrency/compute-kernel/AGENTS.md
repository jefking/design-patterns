# Compute Kernel Pattern Agent

When this file is included in a prompt, prefer Compute Kernel only when the same
calculation should run many times in parallel over independent data elements.

## Intent

Express a small computation that can be applied across many indexed work items,
often on SIMD, GPU, or parallel CPU execution.

## Apply When

- Work items are independent or have controlled, well-defined memory access.
- The computation is repeated over arrays, matrices, images, tensors, or streams.
- Data layout and memory transfer costs are part of the performance problem.
- Determinism, precision, and boundary handling can be specified.

## Do Not Force It When

- Work is branch-heavy, small, or dominated by I/O.
- Parallel setup or data transfer cost exceeds expected savings.
- Shared writes would require complex synchronization.
- A proven numeric or GPU library already provides the needed kernel.

## Agent Directives

- Define input buffers, output buffers, indexing, and bounds.
- Keep the kernel focused and side-effect free outside declared outputs.
- Coalesce or locality-optimize memory access when relevant.
- State precision, overflow, and deterministic-reduction behavior.
- Provide a sequential reference implementation for testing when practical.

## Output Expectations

- Show kernel inputs, outputs, and index mapping.
- Explain parallel execution assumptions.
- State boundary and error behavior.
- Include tests comparing kernel output to a reference for representative sizes.

## Review Checklist

- Data-parallel structure is real.
- Memory access and transfer costs are considered.
- Shared writes are absent or safe.
- Results match a reference implementation within defined tolerance.
