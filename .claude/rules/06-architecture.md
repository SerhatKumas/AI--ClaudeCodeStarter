# Architecture & Design

> Guidance for structuring code and making design decisions. Apply judgment — these
> are heuristics, not laws.

## Guiding heuristics

- **Separation of concerns.** Keep business logic, I/O, and presentation in distinct
  layers. Logic shouldn't know about HTTP; the DB shouldn't know about the UI.
- **Dependency direction points inward.** Core domain logic depends on nothing;
  adapters (DB, web, queue) depend on the core. Not the reverse.
- **Program to interfaces** at module boundaries so implementations can swap.
- **Single source of truth.** One place defines each piece of state/config. Derive,
  don't duplicate.
- **High cohesion, low coupling.** Things that change together live together; things
  that don't, don't.

## SOLID, briefly

- **S** — one reason to change per module.
- **O** — extend without modifying existing code (plugins, strategies).
- **L** — subtypes honor their base type's contract.
- **I** — many small interfaces beat one fat one.
- **D** — depend on abstractions, not concretions.

## Avoid premature abstraction

- **Rule of three:** don't extract a shared abstraction until you've seen the pattern
  ~three times. Two similar things are often coincidence.
- Duplication is cheaper than the *wrong* abstraction. Inline-and-wait beats a leaky
  base class.
- YAGNI: build for the requirements you have, not the ones you imagine.

## Performance

- **Measure first.** Don't optimize on a hunch — profile, find the real hot path.
- Fix algorithmic complexity (the `O(n²)` loop, the N+1 query) before micro-tuning.
- Cache deliberately, with a clear invalidation story. Stale cache > no cache only if
  you understand the staleness.
- Keep the common case fast and the code readable; comment any non-obvious optimization.

## State & data

- Make illegal states unrepresentable (types, enums, constraints) where the language
  allows.
- Prefer immutability; mutate in narrow, well-marked places.
- Push validation to the boundary so the core can trust its inputs.

## Concurrency

- Prefer message passing / well-defined async boundaries over shared mutable state.
- Make operations idempotent where retries are possible.
- Guard shared resources; assume operations can interleave.

## When to surface a decision

If a change implies a new service, a datastore, a public API contract, or a
dependency that's hard to remove later — pause and propose options with trade-offs
before implementing. Record the outcome as an ADR (`05-documentation.md`).
