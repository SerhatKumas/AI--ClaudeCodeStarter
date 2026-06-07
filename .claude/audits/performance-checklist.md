# Performance Checklist

Use when the change touches hot paths, data access, large collections, or rendering.
Measure before optimizing — see `rules/06-architecture.md`.

## Algorithms & data
- [ ] No accidental quadratic behavior (nested loops over the same large set)
- [ ] Appropriate data structures (set/map for lookups, not linear scans)
- [ ] Work done once and reused, not recomputed in a loop
- [ ] Pagination/streaming for large result sets instead of loading everything

## Database
- [ ] No N+1 queries (batch/join/eager-load instead)
- [ ] Queries hit indexes; checked the query plan for slow ones
- [ ] Only the needed columns/rows are selected
- [ ] Transactions scoped tightly; no long locks
- [ ] Connection pooling used; connections released

## I/O & network
- [ ] External calls are batched/parallelized where safe
- [ ] Timeouts and retries (with backoff) on network calls
- [ ] Payloads are reasonably sized; compression where useful

## Caching
- [ ] Caching applied where it measurably helps
- [ ] Cache keys are correct and invalidation is well-defined
- [ ] No caching of user-specific data in a shared cache

## Memory & resources
- [ ] No unbounded growth (caches, queues, in-memory accumulation)
- [ ] Streams/files/handles closed; no leaks
- [ ] Large objects released when no longer needed

## Frontend (if applicable)
- [ ] Avoids unnecessary re-renders / heavy work on the main thread
- [ ] Expensive computations memoized; lists virtualized when large
- [ ] Assets code-split / lazy-loaded; bundle size watched

## Evidence
- [ ] Hot path identified by profiling, not guesswork
- [ ] Before/after numbers captured for any optimization
- [ ] Optimization didn't sacrifice correctness or readability without comment

## Notes
-
