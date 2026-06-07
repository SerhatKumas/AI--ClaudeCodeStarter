# Pre-Release Checklist

Run before tagging a release or deploying to production.

## Code & tests
- [ ] All tests green (unit, integration, E2E for critical flows)
- [ ] Lint and type checks clean
- [ ] Code reviewed and approved
- [ ] No `TODO`/`FIXME`/debug code left in the release path
- [ ] Feature flags for incomplete work are off by default

## Security
- [ ] Security checklist passed for the release's changes
- [ ] Dependency vulnerability scan clean (or findings accepted)
- [ ] No secrets committed; secrets rotated if ever exposed

## Data & migrations
- [ ] DB migrations tested and reversible (or a rollback plan exists)
- [ ] Migrations are backward-compatible with the currently-running version
- [ ] Backups verified before destructive migrations

## Config & infra
- [ ] Required env vars/config documented and set in target environment
- [ ] Third-party keys/quotas valid for production
- [ ] Resource limits, scaling, and timeouts sane for expected load

## Observability
- [ ] Logging, metrics, and error tracking cover the new code paths
- [ ] Alerts exist for the failure modes that matter
- [ ] A dashboard/healthcheck confirms a good deploy

## Release mechanics
- [ ] Version bumped; CHANGELOG/release notes updated
- [ ] Docs updated (README, API docs, runbooks)
- [ ] Rollback plan written and understood
- [ ] Stakeholders/users notified of user-visible changes

## Post-deploy
- [ ] Smoke test the critical paths in production
- [ ] Watch error rates and key metrics for the first window
- [ ] Rollback trigger criteria agreed in advance

## Notes
-
