# Dependencies

> Every dependency is code you didn't write, can't fully see, and must maintain
> forever. Add them deliberately.

## Before adding a dependency, ask

1. **Can the standard library or existing deps already do this?** Check first — most
   projects already pull in a utility lib, an HTTP client, a date lib.
2. **Is it worth it?** A 3-line helper rarely justifies a new package and its
   transitive tree (remember left-pad).
3. **Is it healthy?** Recent commits, real maintainers, reasonable issue response,
   meaningful download counts, a real license.
4. **What's the blast radius?** How many transitive deps does it drag in? What's its
   install size and supply-chain surface?

## When you do add one

- Pin the version (lockfile committed). Don't use floating `latest`.
- Use the exact package name — typosquatting is a real attack vector. Verify the
  publisher.
- Prefer well-established, narrowly-scoped libraries over sprawling frameworks for
  small needs.
- Note *why* it was added in the commit message.

## Keeping them healthy

- Update regularly in small batches, not one terrifying big-bang bump.
- Run the vulnerability scanner (`npm audit`, `pip-audit`, `cargo audit`,
  `osv-scanner`) and triage high-severity findings.
- Remove dependencies you no longer use — dead deps are pure liability.

## License hygiene

- Confirm new deps' licenses are compatible with the project's license.
- Be wary of copyleft (GPL/AGPL) in proprietary codebases — flag it for a human.

## Claude-specific rule

Do **not** add, upgrade, or remove a dependency on your own initiative as a side
effect of another task. If a task seems to need one, propose it and wait for the go
ahead — unless the user already asked for it.
