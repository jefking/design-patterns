# Flyweight Pattern Agent

When this file is included in a prompt, prefer the Flyweight pattern only when
many similar objects can safely share immutable intrinsic state.

## Intent

Reduce memory or object-creation cost by sharing common immutable state and
supplying context-specific extrinsic state at use time.

## Apply When

- A large number of objects repeat the same internal data.
- Memory pressure, allocation cost, or cache locality is a measured or credible concern.
- Shared intrinsic state can be immutable.
- Per-use extrinsic state can be passed in by callers or stored elsewhere.

## Do Not Force It When

- Object counts are small or performance is not a concern.
- Shared state must be mutable per instance.
- The separation between intrinsic and extrinsic state is unclear.

## Agent Directives

- Identify intrinsic state that can be shared safely.
- Identify extrinsic state that must remain outside the flyweight.
- Use a factory, cache, or registry to reuse flyweight instances.
- Make flyweights immutable or defensively protected.
- Avoid hiding global mutable caches without lifecycle and eviction rules.

## Output Expectations

- List intrinsic versus extrinsic fields.
- Show how flyweights are acquired and reused.
- Explain cache key, lifecycle, and eviction decisions if applicable.
- Include tests for reuse, immutability, and behavior with different extrinsic state.

## Review Checklist

- Shared state cannot be mutated through one caller and affect another unexpectedly.
- The memory or allocation benefit is plausible.
- Cache growth is bounded or intentionally process-wide.
- The added complexity is justified by scale.
