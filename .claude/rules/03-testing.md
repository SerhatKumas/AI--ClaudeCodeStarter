# Testing

> Code without tests is a guess. Tests are how we (and Claude) prove a change works.

## The rule

Every behavioral change ships with tests. New feature → new tests. Bug fix →
a test that fails before the fix and passes after (regression test).

## What to test

- **Behavior, not implementation.** Test the public contract; don't assert on private
  internals that refactors will churn.
- **The happy path** — the thing works as intended.
- **The edges** — empty, null, zero, negative, max, unicode, duplicate, concurrent.
- **The failures** — invalid input is rejected with a clear error.
- **The regressions** — every bug gets a test so it can't come back.

## The testing pyramid

```
        /\      few    End-to-end   (slow, brittle, high confidence)
       /  \            Integration  (real wiring, moderate cost)
      /____\    many   Unit         (fast, isolated, run constantly)
```

Favor many fast unit tests, fewer integration tests, and a thin layer of E2E for
critical user journeys.

## Good test shape (Arrange-Act-Assert)

```
test("clamps coupon discount to the subtotal", () => {
  const cart = makeCart({ subtotal: 4_00 });        // Arrange
  const total = applyCoupon(cart, coupon(10_00));   // Act
  expect(total).toBe(0);                            // Assert
});
```

## Principles

- **Deterministic.** No reliance on real time, network, or random without control.
  Inject clocks, seed RNGs, stub external calls.
- **Independent.** Tests pass in any order and don't share mutable state.
- **Fast.** Slow tests don't get run. Keep the unit suite snappy.
- **Readable.** The test name states the expected behavior. A failure should point
  straight at what broke.
- **One reason to fail** per test where practical.

## What NOT to do

- Don't delete or skip a failing test to make CI green — fix the cause.
- Don't write tests that assert what the code *does* just to lock in a bug.
- Don't mock the thing under test; mock its collaborators.
- Don't chase 100% coverage for its own sake — cover behavior that matters.

## Before declaring done

Run the full relevant suite plus lint and typecheck. Report actual results,
including any pre-existing failures you didn't cause.
