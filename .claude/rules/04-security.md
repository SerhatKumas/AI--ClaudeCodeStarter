# Security

> Assume every input is hostile and every secret will leak if you let it.
> This is the rule Claude must never trade away for convenience.

## Secrets

- **Never hardcode** credentials, API keys, tokens, or connection strings.
- Read secrets from environment variables or a secret manager.
- Keep a committed `.env.example` with **placeholder** values; never commit `.env`.
- If you spot a secret in the codebase or git history, flag it immediately — it must
  be rotated, not just deleted.

## Input validation & injection

- Validate and sanitize all external input at the boundary (request body, query
  params, file uploads, env, CLI args).
- **SQL:** parameterized queries / prepared statements only. Never string-concatenate
  SQL.
- **Shell:** avoid shelling out with user input; if unavoidable, use arg arrays, not
  string interpolation.
- **HTML/JS:** escape output by default; rely on the framework's auto-escaping.
  Treat `dangerouslySetInnerHTML` / `v-html` / `innerHTML` as red flags.
- **Paths:** reject `..` and absolute paths in user-supplied filenames; resolve and
  confirm the result stays inside the intended directory.
- **Deserialization:** never deserialize untrusted data into executable objects.

## AuthN / AuthZ

- Authenticate, then **authorize on every request** — verify the caller may touch
  *this* resource, not just that they're logged in.
- Enforce access control server-side; client checks are UX, not security.
- Use vetted libraries for sessions/JWT. Don't roll your own crypto or auth.
- Hash passwords with bcrypt/argon2 — never plain, MD5, or SHA-1.

## Data handling

- Encrypt sensitive data in transit (TLS) and at rest where required.
- Log events, not secrets/PII. Redact tokens, passwords, card numbers.
- Apply least privilege to DB users, cloud IAM, and file permissions.

## Dependencies

- Pin versions; review what you add (see `07-dependencies.md`).
- Run `npm audit` / `pip-audit` / `cargo audit` and address high-severity issues.

## The OWASP-ish quick checklist

- [ ] No secrets in code or logs
- [ ] All inputs validated server-side
- [ ] Queries parameterized
- [ ] Output encoded/escaped
- [ ] AuthZ checked per resource
- [ ] Errors don't leak stack traces / internals to users
- [ ] Dependencies scanned
- [ ] Rate limiting on auth & expensive endpoints

## When unsure

Security mistakes are expensive and hard to reverse. If a change touches auth,
crypto, payments, or PII and you're not certain, stop and flag it for human review.
