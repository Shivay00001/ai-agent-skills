---
name: "uaaf-lean"
description: "Use when the user wants to build an app, feature, MVP, or system (any app idea, \"build me X\", vibe coding). Applies the UAAF-LEAN discipline: bind → think → docs → foundations → security → logic-breaks → ship, with no over-engineering."
---

# UAAF-LEAN — Build Only What's Needed

When the user gives an app/feature idea, follow this in order. Show §1–§3 output for approval BEFORE writing code. If user instructions conflict with §5/§6, flag it — don't silently comply.

## LAW 0 — NO OVER-ENGINEERING
- Build the **smallest thing that completes the core loop end-to-end**. Everything else waits for evidence.
- YAGNI: no feature, abstraction, or infra "for later." Later has better information.
- Boring tech: one frontend, one backend, Postgres. No microservices/Kubernetes/Kafka on day one.
- Smallest diff that closes the ticket. No drive-by refactors. Delete code happily.
- Exception: §4 foundations and §5 security are NOT over-engineering — cheap now, impossible later.
- Replies and docs: minimum words, only what's needed.

## 1. BIND (5 minutes)
Write `BINDING.md`: APP_CLASS · 2 giant analogs (WhatsApp/Uber/Netflix-class competitors) · CORE_LOOP (one sentence) · where users live → which laws (India=DPDP+GST, EU=GDPR, US=CCPA/FTC) · stack (host environment's, else boring default).

## 2. THINK (before any code)
- JTBD: "When I ___, I want to ___, so I can ___."
- Each feature answers 5 gates: strengthens core loop? >10% will use? worth its complexity tax? how will it be abused? removable if it fails?
- Write the NOT-building list (≥5). Giants win by omission — WhatsApp: no stranger search; Netflix: no comments; Uber: masked numbers.
- MVP = smallest complete loop with real users. Loop doesn't close → demo, not MVP.

## 3. DOCS (4 one-pagers, then code)
1. **PRD-lite**: problem, user, must-have features (kill-filtered), out-of-scope, one success metric.
2. **TRD-lite**: stack, folder structure, each third-party service + what happens when it fails, env var names.
3. **Schema + flows**: tables/relations/RLS rules; pages, auth flow, empty/loading/error states.
4. **Plan**: setup → DB → auth → features as vertical slices → polish → deploy, with "done" per phase.
These 4 docs are the source of truth for all code.

## 4. FOUNDATIONS (decide once — saves months)
UUIDs, not sequential ints · UTC everywhere, server time wins · money = integer minor units, never floats · soft-delete + real erase path (DPDP/GDPR) · `/v1` on APIs · idempotency keys wherever money moves or messages send · secrets in env only · one feature-flag mechanism (kill switch).

## 5. SECURITY (every item, every app)
1. No secrets in frontend/repo; `.env` gitignored.
2. Rate limits: auth 5/15min · API 60/min · uploads 5/min; return 429.
3. Server-side validation on every route; parameterized queries only.
4. Ownership check on every object access (IDOR); RLS where supported; identity from session, never request body.
5. bcrypt≥12/argon2 · JWT 15–60min · refresh token in httpOnly cookie · lockout on brute force.
6. CORS whitelist (never `*`) · HTTPS+HSTS · security headers · remove `X-Powered-By`.
7. Uploads: MIME+magic-byte check, size cap, UUID rename, bucket storage, never executable.
8. Errors: generic to users, detailed to logs; no stack traces; no PII in logs.
9. LLM features: keys server-side · max_tokens · per-user budget · sanitize input and output.
10. Pre-deploy: debug off, DB not public, admin behind MFA.

## 6. LOGIC BREAKS (ask per core flow, fix before users find)
- Two clicks at once? → unique constraint / atomic op.
- Retry after timeout? → idempotency key.
- Illegal state jump (refund before payment)? → server-validated state machine; every wait gets a timeout.
- Zero, max, negative, empty, emoji input? → boundary tests.
- Can 1,000 fake accounts farm it? → caps, delayed rewards, device dedup.
- Dependency down? → timeout + honest pending/error state, reconcile later.

## 7. SHIP (the gate)
**Feature done** = happy path + failure paths + authz negative test + validated + errors visible in logs + loading/empty/error states.
**Launch sweep** = privacy policy & T&C live · consent before tracking · OG image · sitemap · store: signed `.aab`, internal→closed testing · subscriptions: price above buy button, cancel ≤2 taps, trial-reminder email 3 days before charge.

## 8. SCALE ONLY ON TRIGGERS
Don't pre-build for scale. When a trigger actually fires, add only that piece: real revenue → pricing/analytics discipline · scale pain → caching/queues/SLOs · enterprise deals → SSO/tenancy/audit · AI in product → eval suite + human gates. Until then, skip it.

