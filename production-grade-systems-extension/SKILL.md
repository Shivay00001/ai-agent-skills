---
name: production-grade-systems-extension
description: >-
  Use this skill as an extension to the production-readiness-audit. It adds an engineering layer focused on modern application systems, production UX patterns, resilient architecture, adaptive technology selection, security hardening, subtle bug detection, failure prevention, performance, observability, caching, and state management.
---

# MASTER PROMPT — PRODUCTION-GRADE SYSTEMS, MODERN ARCHITECTURE & ADAPTIVE PRODUCT ENGINEERING EXTENSION

## CONTINUATION RULE

This is an extension of the previous Production Readiness & Production-Grade App Builder prompt.

DO NOT replace, remove, weaken, contradict, or skip any requirement from the previous prompt.

All previous requirements remain active.

This extension adds another engineering layer focused on:

- modern application systems
- production UX patterns
- resilient architecture
- adaptive technology selection
- security hardening
- subtle bug detection
- logic-break detection
- failure prevention
- performance
- scalability
- observability
- caching
- asynchronous processing
- state management
- resilience
- developer experience
- operational excellence
- competitive feature/system benchmarking
- intelligent architectural decision-making

The goal is not to maximize the number of technologies.

The goal is:

«Build the smallest, smartest, most reliable architecture capable of satisfying the product's actual requirements today while maintaining a clean and credible path to future scale.»

---

## 31. ADAPTIVE ARCHITECTURE ENGINE

Do not blindly follow a predetermined technology stack.

First understand:

- product type
- user types
- traffic patterns
- request patterns
- data volume
- read/write ratio
- real-time requirements
- latency requirements
- availability requirements
- security requirements
- compliance requirements
- geographic distribution
- workload variability
- background processing requirements
- expected growth
- infrastructure budget
- team complexity
- operational capabilities

Then select the architecture.

For every major architectural decision ask:

1. Is it actually needed?
2. What problem does it solve?
3. What simpler alternative exists?
4. What does it cost operationally?
5. What new failure modes does it introduce?
6. Does it improve reliability?
7. Does it improve performance?
8. Does it improve security?
9. Does it improve scalability?
10. Is the complexity justified?

Prefer:

Simple → Modular → Scalable → Distributed only when justified.

Do not introduce microservices merely because the application is expected to grow.

Do not introduce Redis merely because Redis is popular.

Do not introduce queues merely because background jobs exist.

Do not introduce Kubernetes merely because the application is "production."

Every infrastructure component must have a justified purpose.

---

## 32. MODERN STACK SELECTION ENGINE

Evaluate the available modern technologies appropriate to the actual application.

Consider, where relevant:

Frontend

- modern React/Next.js ecosystem
- Vue/Nuxt
- Svelte/SvelteKit
- Angular
- server-rendered applications
- static generation
- hybrid rendering
- progressive enhancement

Backend

- Node.js/TypeScript
- Python
- Go
- Java/Kotlin
- C#
- Rust
- PHP
- Ruby
- framework-native solutions

Database

- PostgreSQL
- MySQL
- SQLite where appropriate
- document databases
- key-value stores
- specialized databases

Caching

- Redis
- in-process caching
- CDN caching
- HTTP caching
- database caching
- distributed cache

Messaging / asynchronous processing

- queues
- job workers
- event-driven processing
- scheduled jobs
- webhook processing

Search

- database-native search
- full-text search
- dedicated search engines
- vector search where genuinely required

Storage

- object storage
- CDN
- image processing
- document storage
- backup storage

Realtime

- WebSockets
- Server-Sent Events
- polling
- managed realtime services

Infrastructure

- serverless
- containers
- VMs
- managed services
- edge infrastructure
- CDN
- reverse proxy
- load balancing

Observability

- structured logs
- metrics
- traces
- error tracking
- profiling
- alerting

Do NOT implement all of these.

Select the best-fit subset.

For each major technology, produce an internal decision:

USE / DO NOT USE / DEFER

with a short technical justification.

---

## 33. ARCHITECTURE COMPLEXITY BUDGET

Treat complexity as a production risk.

Every additional:

- service
- database
- queue
- cache
- dependency
- abstraction
- deployment unit
- infrastructure component
- communication protocol
- background worker

creates additional failure modes.

Before adding one, determine:

Benefit > Complexity + Operational Cost + Failure Risk

If not, don't add it.

Prefer:

Modular monolith > distributed monolith > microservices

unless actual requirements prove otherwise.

---

## 34. REDIS / CACHE INTELLIGENCE SYSTEM

If caching is useful, design it deliberately.

Evaluate:

- Redis
- application memory cache
- CDN cache
- HTTP cache
- database query cache
- computed-data cache

For Redis specifically, determine whether it should handle:

- session storage
- rate limiting
- distributed locks
- caching
- temporary state
- job queues
- idempotency keys
- counters
- realtime presence
- pub/sub

Do not use Redis as the primary source of truth for persistent business data unless explicitly justified.

For every cache implement or evaluate:

- TTL
- invalidation
- stale data behavior
- cache stampede prevention
- cache penetration
- cache poisoning
- memory limits
- eviction policy
- failure behavior
- fallback behavior
- serialization safety
- namespace isolation

Critical rule:

«The application must fail safely when the cache fails unless the cache is intentionally part of the system's required state.»

---

## 35. SMART CACHE STRATEGY

Determine per data type whether to use:

- no cache
- short TTL
- long TTL
- stale-while-revalidate
- write-through
- cache-aside
- precomputed cache
- CDN cache
- browser cache

Do not cache everything.

Cache based on:

cost × frequency × volatility × correctness requirements

Avoid serving dangerously stale data for:

- financial state
- permissions
- security decisions
- inventory
- account balances
- critical configuration

unless the consistency model explicitly permits it.

---

## 36. BACKGROUND JOB & QUEUE SYSTEM

Identify operations that should not block user requests.

Potential candidates:

- emails
- notifications
- image processing
- report generation
- imports
- exports
- large computations
- webhooks
- synchronization
- analytics processing
- document processing
- scheduled maintenance

For jobs, implement where appropriate:

- retries
- exponential backoff
- maximum attempts
- dead-letter handling
- idempotency
- timeout
- cancellation
- job status
- progress tracking
- duplicate prevention
- concurrency control
- observability

Never allow an endlessly retrying job to create an operational disaster.

---

## 37. IDEMPOTENCY SYSTEM

Audit every operation that can accidentally execute more than once.

Especially:

- payments
- subscriptions
- orders
- account creation
- emails
- webhooks
- uploads
- resource creation
- destructive actions
- background jobs

Determine where idempotency keys are required.

Test:

same request × multiple times × concurrent requests

Expected outcome must be explicitly defined.

---

## 38. DISTRIBUTED LOCKING & CONCURRENCY

Where multiple workers or requests can modify the same resource, inspect:

- race conditions
- duplicate processing
- lost updates
- stale writes
- concurrent deletion
- double spending
- double booking
- duplicate notifications

Use appropriate mechanisms:

- database transactions
- row locks
- optimistic concurrency
- version numbers
- unique constraints
- atomic operations
- distributed locks

Do NOT automatically use distributed locks when a database constraint or transaction is sufficient.

---

## 39. MODERN UI RESILIENCE SYSTEM

Every significant UI component should have appropriate:

- loading state
- skeleton state
- empty state
- success state
- partial state
- error state
- retry state
- disabled state
- permission-denied state
- offline state where relevant
- optimistic state where safe
- stale-data indication where relevant

Avoid unnecessary spinners.

Use skeletons when they genuinely improve perceived loading and match the expected content structure.

Do not add skeletons to tiny interactions where they create more visual noise than value.

---

## 40. MICRO-INTERACTION & UX QUALITY SYSTEM

Audit small but important details:

- button feedback
- hover states
- focus states
- pressed states
- disabled states
- validation feedback
- toast behavior
- confirmations
- destructive-action warnings
- undo where appropriate
- autosave feedback
- copy-to-clipboard feedback
- upload progress
- download progress
- retry controls
- pagination feedback
- filter state
- search state
- sorting state
- breadcrumbs
- navigation persistence
- modal behavior
- keyboard shortcuts where useful

Every user action should have understandable feedback.

---

## 41. FORM ENGINEERING

Audit every form.

Handle:

- client validation
- server validation
- field-level errors
- form-level errors
- async validation
- duplicate submissions
- disabled submit
- loading state
- server rejection
- partial completion
- draft state where useful
- autosave where useful
- unsaved changes
- browser autofill
- accessibility
- keyboard navigation
- mobile keyboards

Never rely exclusively on client-side validation.

---

## 42. SEARCH SYSTEM

If search exists, evaluate:

- debouncing
- cancellation of stale requests
- typo tolerance
- ranking
- pagination
- filters
- sorting
- empty results
- no results suggestions
- loading state
- search failure
- query length limits
- abuse protection
- indexing strategy

Prevent:

Request A starts → Request B starts → Request A finishes later → old results overwrite new results.

This class of race condition must be explicitly tested.

---

## 43. PAGINATION & LARGE-DATA SAFETY

Search for every endpoint and UI that can return collections.

Prevent:

- unbounded queries
- loading thousands/millions of records
- accidental full-table scans
- giant JSON responses
- browser memory exhaustion
- slow rendering

Choose appropriately between:

- offset pagination
- cursor pagination
- infinite scrolling
- virtualized lists
- chunked processing

Do not use infinite scrolling merely because it is fashionable.

---

## 44. FILE & MEDIA SYSTEM

If the application handles files, audit:

- MIME validation
- extension validation
- file-size limits
- filename sanitization
- path traversal
- malicious uploads
- executable content
- archive bombs
- image bombs
- metadata leakage
- access control
- signed URLs
- upload expiration
- download authorization
- virus/malware scanning where appropriate
- storage isolation
- deletion
- orphan cleanup
- resumable uploads
- progress reporting

Never trust:

- filename
- extension
- MIME type supplied by client
- client-side file validation

---

## 45. NOTIFICATION SYSTEM

If notifications exist, design:

- email
- push
- in-app
- SMS where applicable

with:

- preference management
- unsubscribe
- deduplication
- retry
- failure handling
- rate limiting
- batching
- templates
- localization
- delivery status
- user timezone handling
- quiet periods where appropriate

Do not send duplicate notifications because multiple workers processed the same event.

---

## 46. WEBHOOK SYSTEM

For incoming webhooks:

- verify signatures
- validate payloads
- enforce timestamp/replay protection where supported
- authenticate source
- store event identifiers
- deduplicate
- process asynchronously when appropriate
- acknowledge safely
- retry failures
- preserve raw event data only when appropriate and secure
- monitor failures

Assume:

webhooks can arrive late, twice, out of order, malformed, or not at all.

Design accordingly.

---

## 47. RATE LIMITING & ABUSE CONTROL

Implement appropriate controls for:

- login
- password reset
- registration
- search
- expensive APIs
- file uploads
- AI/API calls
- email sending
- OTP
- public endpoints
- resource creation

Consider:

- IP-based limits
- account-based limits
- endpoint-based limits
- token buckets
- sliding windows
- distributed rate limits

Avoid rate limits that accidentally lock out legitimate users.

Return appropriate retry information where useful.

---

## 48. AI FEATURE SAFETY — IF APPLICABLE

If AI functionality exists, audit:

- prompt injection
- data leakage
- unauthorized tool usage
- excessive token usage
- runaway costs
- malicious inputs
- unsafe outputs
- model failures
- timeout
- retries
- hallucination-sensitive workflows
- structured output validation
- tool authorization
- model fallback
- rate limiting
- abuse
- prompt/version management

Never trust model output as inherently valid.

Validate AI-generated:

- JSON
- commands
- SQL
- URLs
- tool arguments
- business decisions
- user-visible content

before acting on it.

---

## 49. REALTIME SYSTEM

If realtime behavior is required, choose between:

- polling
- long polling
- SSE
- WebSockets
- managed realtime infrastructure

based on actual requirements.

Audit:

- reconnection
- heartbeat
- connection limits
- authentication
- authorization
- stale connections
- duplicate messages
- message ordering
- missed events
- backpressure
- resource cleanup

The application must recover gracefully from:

disconnect → reconnect → missed messages → synchronization.

---

## 50. OFFLINE / NETWORK RESILIENCE

Where appropriate, handle:

- slow network
- intermittent connection
- timeout
- offline state
- reconnect
- retry
- duplicate submission
- stale data

Do not automatically implement full offline-first architecture unless the product benefits from it.

---

## 51. STATE MANAGEMENT AUDIT

Identify:

- server state
- client state
- URL state
- form state
- session state
- persistent state
- temporary state

Avoid storing the same state in multiple places unnecessarily.

Detect:

- stale state
- duplicated state
- synchronization bugs
- memory leaks
- inconsistent state
- race conditions

Prefer a single source of truth wherever practical.

---

## 52. SECURITY-CRITICAL UI/LOGIC SEPARATION

Never trust:

- hidden fields
- disabled buttons
- frontend routes
- local storage
- cookies without proper server validation
- client-side roles
- client-side pricing
- client-side limits
- client-side permissions

Any security-sensitive decision must be independently enforced by the backend.

---

## 53. MODERN ERROR RECOVERY

Instead of simply displaying an error, determine whether the application can safely:

- retry
- refresh
- recover state
- rollback optimistic changes
- resume upload
- restore draft
- reconnect
- reauthenticate
- redirect
- provide support information
- preserve user input

Error recovery should be proportional to the failure.

---

## 54. ERROR BOUNDARY & CRASH CONTAINMENT

Prevent one component failure from crashing the entire application where the architecture permits isolation.

Implement appropriate:

- frontend error boundaries
- API exception boundaries
- worker isolation
- process supervision
- graceful shutdown
- request timeouts
- circuit breakers where justified

A crash should produce:

controlled failure + useful diagnostics + recovery path

rather than:

blank screen + lost state + mystery.

---

## 55. CIRCUIT BREAKER / BULKHEAD / RESILIENCE PATTERNS

Where external dependencies are unreliable, evaluate:

- timeout
- retry
- exponential backoff
- circuit breaker
- bulkhead isolation
- fallback
- queue-based buffering

Do not blindly add retries.

Retries can amplify outages.

Use:

timeout + bounded retry + backoff + jitter + failure limit

where appropriate.

---

## 56. DATABASE RESILIENCE

Evaluate:

- connection pool limits
- query timeout
- transaction timeout
- deadlocks
- retries
- migration safety
- schema compatibility
- long-running queries
- connection exhaustion
- replication lag where applicable

Never allow a traffic spike to exhaust the database connection pool and cascade into total application failure.

---

## 57. DEPLOYMENT-SAFE DATABASE MIGRATIONS

For production migrations, evaluate whether the migration is:

- backward compatible
- reversible where practical
- safe during rolling deployment
- safe with old application versions
- safe with new application versions

Prefer:

expand → migrate → contract

for schema changes that require compatibility across versions.

---

## 58. FEATURE FLAG SYSTEM

Where useful, support controlled rollout through:

- feature flags
- percentage rollout
- user targeting
- environment targeting
- emergency disable
- gradual release

Every flag should have:

- owner
- purpose
- default behavior
- cleanup plan

Do not accumulate permanent dead flags.

---

## 59. AUDIT LOGGING

For security-sensitive or business-critical operations, determine whether an immutable or appropriately protected audit trail is needed.

Potential events:

- login
- privilege changes
- account changes
- payment events
- destructive actions
- configuration changes
- administrative actions
- API-key changes
- security events

Audit logs should answer:

Who → did what → to what → when → from where/context → result

without unnecessarily storing sensitive data.

---

## 60. SECRET & CREDENTIAL SAFETY

Search the repository and configuration for:

- API keys
- tokens
- passwords
- private keys
- cloud credentials
- database credentials
- test secrets

Check:

- git history where appropriate
- build artifacts
- logs
- client bundles
- source maps
- error reporting
- environment configuration

Never place server-only secrets into client-exposed environments.

If an exposed secret is discovered, treat it as compromised and recommend/perform rotation when authorized.

---

## 61. HTTP & NETWORK HARDENING

Evaluate:

- HTTPS
- HSTS
- secure cookies
- SameSite
- CORS
- CSP
- X-Content-Type-Options
- Referrer-Policy
- Permissions-Policy
- clickjacking protection
- request size limits
- response size limits
- timeout
- compression
- caching headers

Only enable security mechanisms according to actual application behavior; avoid configurations that break legitimate functionality.

---

## 62. RESOURCE EXHAUSTION DEFENSE

Look for:

- infinite loops
- giant payloads
- huge uploads
- regex denial-of-service
- unbounded recursion
- excessive database queries
- memory-heavy operations
- expensive AI requests
- expensive image processing
- unlimited pagination
- unlimited exports
- unlimited concurrent jobs

Every expensive operation needs reasonable limits.

---

## 63. SMART DEFAULTS

Design safe defaults for:

- permissions
- privacy
- rate limits
- timeouts
- retries
- cache TTL
- pagination
- upload size
- session lifetime
- logging
- feature availability

Defaults should fail toward the safer state.

---

## 64. COMPETITOR & BEST-IN-CLASS SYSTEM BENCHMARKING

Do not blindly copy competitors.

Identify relevant:

- direct competitors
- category leaders
- mature SaaS products
- highly reliable consumer apps
- modern developer platforms
- comparable open-source systems

Study their systems and patterns, not merely their visual appearance.

Look for:

- onboarding
- authentication
- navigation
- search
- filtering
- dashboards
- loading behavior
- skeletons
- empty states
- error recovery
- notifications
- permissions
- billing
- settings
- import/export
- activity history
- audit logs
- realtime behavior
- offline behavior
- accessibility
- responsive behavior
- performance patterns
- account recovery
- support mechanisms

Extract reusable patterns.

Do NOT copy proprietary implementation details, protected code, branding, or intellectual property.

---

## 65. FEATURE PARITY VS FEATURE BLOAT

For every discovered competitor feature classify:

MUST HAVE

Necessary for credible product operation.

SHOULD HAVE

Strong user-value feature.

NICE TO HAVE

Useful but nonessential.

NOT RELEVANT

Doesn't fit the product.

DANGEROUS COMPLEXITY

Would add disproportionate maintenance or failure risk.

Only implement justified features.

---

## 66. "SMALL THINGS" AUDIT

Perform a dedicated pass for details developers commonly overlook:

- favicon
- app icons
- metadata
- loading indicators
- skeletons
- empty states
- error pages
- 404
- 403
- 429
- 500
- maintenance state
- confirmation messages
- success messages
- button disabled state
- keyboard focus
- copy feedback
- date formatting
- number formatting
- currency formatting
- timezone handling
- pluralization
- text overflow
- long usernames
- long emails
- unusual characters
- emoji
- localization readiness
- browser refresh
- direct URL access
- back button
- session expiry
- duplicate clicks
- double taps
- slow API
- no API response
- partial API response
- malformed API response
- deleted records
- archived records
- permissions changing while user is active

Small bugs are still production bugs.

---

## 67. TIME, DATE & TIMEZONE SYSTEM

Audit:

- UTC storage
- timezone conversion
- daylight-saving behavior where applicable
- date-only values
- timestamps
- recurring events
- expiration
- token lifetime
- scheduled jobs
- user timezone
- server timezone

Never assume:

server timezone = user timezone

Never use ambiguous date formats for important business data.

---

## 68. INTERNATIONALIZATION READINESS

Even if the application initially supports one language, avoid architecture that makes future localization unnecessarily difficult.

Check:

- hardcoded text
- text expansion
- date formats
- currency
- number formatting
- RTL considerations where relevant
- pluralization

Do not implement full internationalization unless there is a credible requirement.

---

## 69. ACCESSIBILITY DEEP PASS

Beyond basic accessibility, inspect:

- semantic hierarchy
- screen-reader announcements
- dynamic content
- modal focus trapping
- focus restoration
- keyboard-only workflows
- form error association
- accessible names
- reduced motion
- zoom
- touch interaction
- contrast
- status messages

Critical flows must remain usable without relying exclusively on a mouse or visual cues.

---

## 70. MOBILE & RESPONSIVE FAILURE PASS

Test unusual viewport conditions:

- small phone
- large phone
- tablet
- desktop
- wide desktop
- zoomed interface
- landscape
- portrait

Check:

- overflow
- sticky elements
- modals
- tables
- forms
- navigation
- dropdowns
- keyboard interaction
- touch targets

Do not merely test one "mobile" viewport.

---

## 71. PERFORMANCE BUDGETS

Where appropriate establish practical budgets for:

- initial page load
- JavaScript
- CSS
- images
- API latency
- database queries
- largest content
- interaction latency
- memory
- background jobs

If a budget is exceeded:

identify why → determine impact → optimize if justified.

Do not optimize arbitrary metrics without user/business relevance.

---

## 72. COST-AWARE ARCHITECTURE

For every infrastructure component estimate:

- baseline cost
- variable cost
- scaling cost
- operational burden

Look for opportunities to use:

- managed services
- existing infrastructure
- CDN
- caching
- batching
- asynchronous jobs
- efficient queries
- appropriate storage tiers

Do not optimize cost by creating fragile architecture.

---

## 73. SMART FALLBACK ARCHITECTURE

For noncritical dependencies, define fallback behavior.

Example:

Primary service → timeout → bounded retry → fallback/cache/degraded mode → user-visible state

The fallback itself must not introduce security or data-integrity problems.

---

## 74. DATA CONSISTENCY CLASSIFICATION

For important data, classify consistency requirements:

- strongly consistent
- eventually consistent
- session consistent
- best-effort

Do not accidentally introduce eventual consistency into security- or money-critical operations.

---

## 75. EVENT SYSTEM

If an event architecture is appropriate, distinguish:

- commands
- events
- queries
- domain events
- integration events

Prevent:

- circular events
- duplicate processing
- event storms
- hidden coupling
- undocumented event contracts

Use events only where they provide genuine architectural value.

---

## 76. API CONTRACT STABILITY

Protect clients from unnecessary breaking changes.

Evaluate:

- versioning
- schema validation
- backward compatibility
- deprecation
- error contracts
- pagination contracts
- field evolution

When changing APIs, consider:

old client + new server

and, where required:

new client + old server

---

## 77. BACKWARD COMPATIBILITY

Before changing:

- database schema
- API contracts
- authentication
- serialized data
- storage formats
- queue payloads

check whether existing records, clients, workers, or deployments depend on the old behavior.

---

## 78. RECOVERY-FIRST DESIGN

For every critical operation ask:

«"If this fails halfway through, how does the system recover?"»

Define:

- rollback
- retry
- compensation
- reconciliation
- manual recovery
- idempotent replay

A system that works only when every operation succeeds is not production-grade.

---

## 79. RECONCILIATION SYSTEM

For important asynchronous or external operations, consider periodic reconciliation.

Examples:

- payment status
- subscription state
- inventory
- external integrations
- webhook processing
- background jobs

Detect:

local state ≠ external state

and safely repair or flag the mismatch.

---

## 80. GRACEFUL SHUTDOWN

Ensure services/workers can:

1. stop accepting new work
2. finish safe in-flight work
3. close connections
4. flush logs/telemetry
5. terminate cleanly
6. restart safely

Test shutdown during:

- API requests
- background jobs
- database operations
- external requests

---

## 81. STARTUP & BOOT VALIDATION

At startup validate critical:

- configuration
- environment
- database connectivity
- required services
- schema compatibility
- secrets
- application version

Fail fast for impossible-to-run configurations.

Do not fail startup for optional dependencies unless the application genuinely requires them.

---

## 82. HEALTH & READINESS MODEL

Separate:

Liveness

"Is the process alive?"

Readiness

"Can this instance safely receive traffic?"

Dependency health

"What dependencies are failing?"

Do not create health checks that create additional system load or falsely report health.

---

## 83. INCIDENT READINESS

Prepare the application for real incidents.

Document:

- common failures
- rollback
- recovery
- database recovery
- secret rotation
- dependency outage
- elevated error rates
- suspicious activity
- queue backlog
- performance degradation

Where appropriate create runbooks.

---

## 84. SECURITY INCIDENT READINESS

Determine how the system would respond to:

- credential leak
- account takeover
- suspicious login
- API abuse
- data exposure
- malicious upload
- compromised dependency
- webhook abuse

Identify:

- logging
- detection
- containment
- revocation
- rotation
- recovery

---

## 85. TEST MATRIX EXPANSION

Do not only test normal inputs.

For critical functionality test:

Normal × Empty × Null × Missing × Huge × Tiny × Duplicate × Malformed × Unauthorized × Expired × Concurrent × Slow × Timeout × Failure × Retry

Where applicable.

---

## 86. PROPERTY & INVARIANT THINKING

Identify business invariants.

Examples:

- balance cannot become negative
- unique username remains unique
- deleted resource cannot be modified
- unauthorized user cannot access private resource
- payment cannot be captured twice
- quota cannot be exceeded
- job cannot execute twice

Test the invariant rather than merely testing the UI.

---

## 87. FUZZING / ADVERSARIAL INPUT

Where practical, test unusual:

- strings
- Unicode
- malformed JSON
- nested objects
- extremely long input
- unexpected types
- boundary numbers
- negative numbers
- floating-point values
- dates
- encoded URLs

The application should reject invalid input safely.

---

## 88. SECURITY THROUGH DEPTH

Do not rely on one protection.

Critical systems should use layered controls:

Input validation + authorization + database constraints + rate limiting + monitoring + safe failure

where appropriate.

---

## 89. LOGGING INTELLIGENCE

Avoid both extremes:

Too little

Impossible to diagnose incidents.

Too much

Expensive, noisy, insecure, and useless.

Log:

- meaningful lifecycle events
- failures
- security events
- important business transitions
- correlation IDs
- relevant identifiers

Never log:

- passwords
- tokens
- secrets
- unnecessary sensitive information

---

## 90. PRODUCTION DEBUGGING SYSTEM

Every serious failure should be diagnosable from:

timestamp + request/correlation ID + component + operation + sanitized context + error + stack/trace

where appropriate.

---

## 91. DEAD CODE & SYSTEM CLEANUP

After hardening, remove:

- dead code
- unused imports
- abandoned experiments
- duplicate utilities
- obsolete feature flags
- unused dependencies
- debug routes
- development-only shortcuts
- temporary hacks

Do not remove code unless you can establish that it is safe to remove.

---

## 92. ARCHITECTURE DOCUMENTATION

Create a concise architecture document covering:

- system components
- data flow
- trust boundaries
- external dependencies
- database
- caching
- queues
- authentication
- authorization
- deployment
- observability
- failure recovery

The diagram/documentation must reflect reality.

---

## 93. DECISION RECORD SYSTEM

For significant decisions record:

Problem → Options → Decision → Why → Tradeoffs → Future trigger for reconsideration

Examples:

- why Redis exists
- why Redis does not exist
- why a queue exists
- why microservices are avoided
- why a database was selected
- why a particular rendering strategy was chosen

This prevents future developers from blindly copying architecture.

---

## 94. ADAPTIVE TECHNOLOGY REPLACEMENT

If the existing stack is inappropriate, outdated, insecure, fragile, or unnecessarily complex:

1. identify the problem
2. assess migration risk
3. compare alternatives
4. determine whether replacement is justified
5. prefer incremental migration
6. preserve existing functionality
7. test compatibility
8. migrate only when the benefit clearly exceeds migration risk

Never rewrite the entire application merely because a newer framework exists.

---

## 95. NO-OVERENGINEERING RULE

Before adding any technology ask:

What exact production problem does this solve?

If there is no strong answer:

DO NOT ADD IT.

Examples:

Redis is justified by a real caching/rate-limit/session/coordination requirement.

A queue is justified by real asynchronous workloads.

WebSockets are justified by real realtime requirements.

Microservices are justified by real organizational/scaling/deployment boundaries.

A search engine is justified by real search requirements.

A Kubernetes cluster is justified by actual infrastructure needs.

Otherwise prefer simpler architecture.

---

## 96. FINAL ARCHITECTURE OPTIMIZATION PASS

After implementing the required systems, perform another pass specifically asking:

«"Can this architecture be made simpler without losing security, reliability, performance, or scalability?"»

Remove unnecessary complexity.

The final architecture should be:

Secure + Reliable + Observable + Maintainable + Efficient + Scalable + Understandable

not:

Technologically impressive but operationally fragile.

---

## 97. FINAL SYSTEM-BY-SYSTEM SCORECARD

Produce a final matrix:

System| Required?| Implemented?| Verified?| Technology| Complexity| Risk| Status
Authentication| | | | | | | 
Authorization| | | | | | | 
Database| | | | | | | 
Cache| | | | | | | 
Redis| | | | | | | 
Queue| | | | | | | 
Background jobs| | | | | | | 
Search| | | | | | | 
Storage| | | | | | | 
Realtime| | | | | | | 
Notifications| | | | | | | 
Webhooks| | | | | | | 
Rate limiting| | | | | | | 
Audit logging| | | | | | | 
Monitoring| | | | | | | 
Error tracking| | | | | | | 
CI/CD| | | | | | | 
Backups| | | | | | | 
Disaster recovery| | | | | | | 
Feature flags| | | | | | | 
Accessibility| | | | | | | 
Responsive UX| | | | | | | 
Skeleton/loading system| | | | | | | 
Empty/error states| | | | | | | 
Offline resilience| | | | | | | 
AI safety| | | | | | | 
Performance| | | | | | | 
Security| | | | | | | 

---

## 98. COMPETITIVE SYSTEM GAP ANALYSIS

After examining relevant comparable products, create:

Capability| Our Product| Best Comparable Pattern| Gap| Value| Complexity| Decision

Only implement a competitive pattern when it improves:

- user value
- reliability
- usability
- security
- conversion
- retention
- operational quality

Do not add features simply to increase feature count.

---

## 99. FINAL "NOTHING BROKE" REGRESSION PASS

This is mandatory.

After every significant change:

Re-test previously working systems.

Especially:

- authentication
- navigation
- database operations
- permissions
- core workflows
- APIs
- forms
- payments
- integrations
- uploads
- notifications
- search
- background jobs

Use regression tests wherever possible.

The rule is:

«Fixing one system must not silently break another system.»

---

## 100. FINAL PRODUCTION SIMULATION

Before declaring completion, simulate the application as if it were already serving real users.

Test:

Normal user

Registration → login → core workflow → logout

Returning user

Login → existing data → update → refresh → logout

Unauthorized user

Attempt protected actions.

Malicious user

Manipulate requests, IDs, roles, inputs, limits.

Slow network

Use delayed responses.

Failed dependency

Simulate API/database/cache/queue failures where safely possible.

Concurrent users

Attempt conflicting operations.

Duplicate requests

Repeat mutations.

Deployment

Start new version against existing data.

Rollback

Return to previous version where feasible.

Recovery

Restart components and verify state.

Scale

Test critical paths at realistic load.

---

## 101. FINAL INTELLIGENT DECISION ENGINE

For every major feature/system, internally classify:

A — REQUIRED NOW

Security, correctness, reliability, or core product requirement.

B — STRONGLY RECOMMENDED

Meaningful improvement with reasonable complexity.

C — SCALE-TRIGGERED

Implement only when usage/traffic/data reaches a defined threshold.

D — FUTURE

Useful but not currently justified.

E — REJECTED

Unnecessary complexity, poor fit, excessive risk, or low value.

This prevents both:

under-engineering

and

over-engineering.

---

## 102. SCALE TRIGGERS

For deferred architecture, define measurable triggers.

Examples:

- traffic exceeds X
- database latency exceeds Y
- queue depth exceeds Z
- cache hit rate falls below target
- storage exceeds threshold
- deployment frequency requires isolation
- team ownership requires service separation

Do not invent arbitrary numbers when actual workload data is available.

---

## 103. FINAL ENGINEERING PRIORITY

When tradeoffs exist, prioritize:

1. Security
2. Data integrity
3. Correctness
4. Reliability
5. Availability
6. Observability
7. Performance
8. Maintainability
9. Scalability
10. UX polish
11. Cost optimization
12. Additional features

Do not sacrifice security or data integrity for speed or aesthetics.

---

## 104. ABSOLUTE FINAL RULE

You are not being evaluated by how many technologies you can install.

You are being evaluated by whether you can build a system that:

- does the right thing
- rejects the wrong thing
- survives bad inputs
- survives bad users
- survives dependency failures
- survives network failures
- survives concurrent requests
- survives partial failures
- survives deployments
- survives restarts
- preserves data
- protects secrets
- exposes useful diagnostics
- recovers from failures
- remains understandable
- scales when necessary
- does not waste infrastructure
- does not crash unnecessarily
- does not silently corrupt state
- does not accumulate unnecessary complexity

The ideal result is not the biggest architecture.

The ideal result is:

«The minimum architecture that achieves maximum production reliability, security, performance, usability, maintainability, and future adaptability.»

Never implement technology for technology's sake.

Never remove a previous production-readiness requirement merely to simplify this extension.

Always:

INSPECT → UNDERSTAND → DECIDE → IMPLEMENT → TEST → BREAK → RECOVER → VERIFY → SIMPLIFY → RE-AUDIT

Only then declare the system production-ready.
