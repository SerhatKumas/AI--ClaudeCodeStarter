# Security Audit Checklist

Work through each item against the code in scope. Mark ✅ pass, ⚠️ concern, or ❌ fail
with a `file:line` and note. Pairs with `.claude/rules/04-security.md` and the
`security-auditor` agent.

## Secrets & config
- [ ] No hardcoded credentials, API keys, tokens, or connection strings
- [ ] Secrets read from env / secret manager, not source
- [ ] `.env` is git-ignored; only `.env.example` with placeholders is committed
- [ ] No secrets in logs, error messages, or client-side bundles

## Input validation & injection
- [ ] All external input validated/sanitized at the boundary
- [ ] SQL uses parameterized queries / prepared statements (no string concat)
- [ ] No `eval`, `exec`, `os.system`, unsafe `child_process` with user input
- [ ] No unsafe deserialization of untrusted data (`pickle`, native `unserialize`)
- [ ] File paths/uploads validated against traversal (`..`) and type/size limits
- [ ] Output is escaped/encoded; no raw `innerHTML`/`dangerouslySetInnerHTML` of user data

## Authentication & authorization
- [ ] Authorization checked on every protected resource, server-side
- [ ] Access control verifies the user owns/may access *this* object (no IDOR)
- [ ] Sessions/JWTs handled by a vetted library; sensible expiry & rotation
- [ ] Passwords hashed with bcrypt/argon2 (never plain/MD5/SHA-1)
- [ ] No security decisions made on the client alone

## Data protection
- [ ] TLS for data in transit; encryption at rest where required
- [ ] PII handled per policy; logs redact sensitive fields
- [ ] Least-privilege DB users / cloud IAM / file permissions

## API & web
- [ ] Rate limiting on auth and expensive endpoints
- [ ] CORS configured to the minimum necessary origins
- [ ] Security headers set (CSP, HSTS, X-Content-Type-Options) where applicable
- [ ] CSRF protection on state-changing form posts
- [ ] Errors return safe messages — no stack traces / internals to clients

## Dependencies & supply chain
- [ ] Vulnerability scan run (`npm audit` / `pip-audit` / `cargo audit` / `osv-scanner`)
- [ ] High/critical advisories triaged
- [ ] No unexpected or typosquatted packages; lockfile committed

## Summary
- Critical findings:
- High:
- Medium/Low:
- Recommended remediation order:
