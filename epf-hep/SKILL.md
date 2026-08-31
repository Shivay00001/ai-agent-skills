---
name: epf-hep
description: Elite Production Forensics, Failure Intelligence & Hidden Engineering Practices Engine. Investigates the undocumented, under-taught, and hidden parts of software engineering discovered through production failures and mature engineering processes.
---

# EPF-HEP — Elite Production Forensics, Failure Intelligence & Hidden Engineering Practices Engine

## 1. PURPOSE

Create an elite engineering intelligence skill that investigates the parts of software engineering that are frequently:

- undocumented
- under-taught
- ignored
- misunderstood
- discovered only after production failures
- learned through expensive incidents
- known primarily through experienced engineering organizations
- hidden inside mature engineering processes
- buried inside standards, incident reports, source code, technical papers, postmortems, changelogs, security advisories, and production experience

The skill must discover these practices and determine whether they are relevant to the current product.

It must investigate from:

the smallest implementation detail

to:

the largest distributed architecture

without assuming that complexity is automatically better.

## 2. ABSOLUTE PRINCIPLE

Do NOT interpret:

«"hidden engineering"»

as:

- proprietary secrets
- stolen source code
- confidential information
- unauthorized access
- private company systems
- leaked credentials
- exploit instructions
- confidential architecture diagrams

The engine must instead derive legitimate engineering knowledge from:

- public technical documentation
- standards
- public postmortems
- vulnerability disclosures
- academic research
- open-source implementations
- engineering blogs
- public incident reports
- public architecture discussions
- official platform documentation
- reproducible experiments
- industry practices

Never fabricate secret knowledge.

## 3. THE REAL QUESTION

For every system ask:

«What do inexperienced engineers usually build?»

Then:

«What does a mature production organization do differently?»

Then:

«Why?»

Then:

«What evidence proves the difference matters?»

Then:

«Does this product actually need it?»

## 4. PRODUCTION-REALITY GAP ENGINE

Identify the difference between:

Tutorial Quality
↓
Prototype Quality
↓
MVP Quality
↓
Production Quality
↓
High-Scale Production Quality
↓
Mission-Critical Quality

For every subsystem determine its actual maturity.

Never claim:

«production-ready»

without evidence.

## 5. 0–100 ENGINEERING MATURITY MODEL

Score every relevant area from:

0–19  Dangerous / absent
20–39 Weak
40–59 Basic
60–69 Functional
70–79 Production-capable
80–89 Strong production quality
90–94 Elite
95–99 Exceptional
100    Verified against defined acceptance criteria

IMPORTANT:

100 does NOT mean mathematically perfect or impossible to break.

It means:

«all defined acceptance criteria have been independently verified to the chosen assurance level.»

## 6. NO-FALSE-100 RULE

Never assign 100 because:

- code looks clean
- tests pass
- an AI says so
- scanners are clean
- deployment succeeded
- no bugs were found

A score requires evidence.

## 7. GLOBAL SYSTEM BREAKDOWN

Decompose the product into:

Product
├── Users
├── Requirements
├── UX
├── Frontend
├── Backend
├── APIs
├── Authentication
├── Authorization
├── Data
├── Database
├── Cache
├── Queue
├── Storage
├── Search
├── AI
├── Networking
├── Infrastructure
├── Deployment
├── CI/CD
├── Observability
├── Security
├── Compliance
├── Backup
├── Recovery
├── Support
├── Billing
├── Analytics
├── Administration
├── Documentation
└── Governance

Then recursively decompose every subsystem.

## 8. MINIATURE-DECOMPOSITION ENGINE

Never review only:

«"backend"»

Break it into:

Request
↓
DNS
↓
TLS
↓
Load balancer
↓
Gateway
↓
Authentication
↓
Authorization
↓
Validation
↓
Rate limiting
↓
Controller
↓
Service
↓
Domain logic
↓
Database
↓
Cache
↓
Queue
↓
External dependency
↓
Response
↓
Logging
↓
Metrics
↓
Tracing

Then inspect each transition.

## 9. TRUST-BOUNDARY ENGINE

Map every trust boundary.

Examples:

User
→ Browser

Browser
→ API

API
→ Database

Application
→ External API

Application
→ Cloud

Developer
→ CI/CD

CI/CD
→ Production

AI Agent
→ Tools

Service
→ Service

For every boundary ask:

- What can cross?
- Who can cross?
- What authentication is required?
- What authorization is required?
- What validation occurs?
- What could be injected?
- What data can leak?
- What happens when trust is violated?

## 10. ASSUME-BREACH ENGINE

Do not design around:

«"The attacker won't get this far."»

Instead ask:

«What happens if this boundary is already compromised?»

Evaluate:

- lateral movement
- privilege escalation
- credential reuse
- token theft
- service compromise
- database compromise
- CI/CD compromise
- insider misuse

Design containment.

## 11. BLAST-RADIUS ENGINE

For every credential, service, component, and dependency determine:

If compromised:
↓
What can it access?
↓
What can it modify?
↓
What can it delete?
↓
What secrets can it obtain?
↓
How far can compromise spread?

Minimize blast radius.

## 12. "ONE FAILURE AWAY" TEST

For every critical component ask:

«If this component disappears right now, what happens?»

Test:

- database failure
- cache failure
- queue failure
- DNS issue
- network issue
- identity provider failure
- payment provider failure
- email provider failure
- storage failure
- model provider failure
- deployment failure
- certificate failure

The system must have an intentional response.

## 13. DEPENDENCY FAILURE MATRIX

Create:

Dependency| Failure| Detection| User Impact| Fallback| Recovery

Do this for every meaningful external dependency.

## 14. CHAOS-READINESS ENGINE

Where appropriate, perform controlled failure testing.

Potential experiments:

- kill service
- disconnect dependency
- delay network
- inject timeout
- return malformed response
- exhaust resource
- restart process
- simulate database unavailability

Never perform destructive production experiments without explicit authorization and appropriate safeguards.

## 15. PRODUCTION INCIDENT INTELLIGENCE

Search public incident knowledge for analogous failures.

Look for patterns such as:

- cascading failures
- retry storms
- cache stampedes
- thundering herd
- database connection exhaustion
- certificate expiration
- DNS failure
- clock skew
- queue backlog
- dead-letter accumulation
- configuration mistakes
- feature-flag errors
- bad migrations
- accidental data deletion
- dependency outages
- supply-chain compromise
- authorization failures
- logging overload

Convert incidents into preventive controls.

## 16. "PEOPLE REGRET THIS LATER" ENGINE

Identify decisions that commonly create future pain:

- premature microservices
- excessive abstraction
- undocumented assumptions
- shared mutable state
- weak migration strategy
- no rollback
- no ownership model
- hidden dependencies
- hard-coded configuration
- missing idempotency
- unbounded retries
- unbounded queues
- unlimited resource consumption
- poor observability
- secrets embedded in code
- no data retention policy
- no deletion strategy
- no compatibility strategy
- vendor lock-in without exit strategy

Do NOT automatically reject these technologies.

Determine whether the current implementation contains the associated failure mode.

## 17. "TOP ENGINEER DIFFERENCE" ENGINE

For every subsystem ask:

Basic implementation

What would a beginner probably build?

Competent implementation

What would an experienced developer build?

Mature production implementation

What additional safeguards would a strong production organization add?

Elite implementation

What failure modes, operational realities, and long-term evolution concerns would a highly experienced team consider?

Then determine which level is actually necessary.

## 18. NEGATIVE-SPACE ENGINEERING

Do not only ask:

«What should we build?»

Also ask:

«What should we deliberately NOT build?»

Identify:

- unnecessary services
- unnecessary dependencies
- unnecessary databases
- unnecessary caches
- unnecessary abstractions
- unnecessary APIs
- unnecessary permissions
- unnecessary background jobs
- unnecessary data collection
- unnecessary telemetry
- unnecessary infrastructure

Removing unnecessary systems improves security and reliability.

## 19. ANTI-FEATURE ENGINE

For every proposed feature:

Benefit
↓
Complexity
↓
Security surface
↓
Maintenance
↓
Operational cost
↓
Failure modes

If the feature creates more problems than value:

REJECT

## 20. "SILLY FAILURE" ENGINE

Search for tiny defects that can create disproportionate damage:

- wrong environment variable
- wrong region
- wrong timezone
- wrong currency
- wrong default
- wrong permission
- wrong HTTP status
- wrong cache TTL
- wrong retry count
- wrong timeout
- missing index
- missing constraint
- wrong database migration order
- incorrect null handling
- race condition
- duplicate event
- stale cache
- stale token
- incorrect pagination
- off-by-one errors
- malformed error handling
- incorrect URL
- wrong CORS configuration
- debug configuration in production

## 21. EDGE-CASE MATRIX

For every core workflow test:

Empty
Null
Zero
Negative
Maximum
Minimum
Duplicate
Malformed
Expired
Concurrent
Repeated
Out-of-order
Interrupted
Unauthorized
Partially authorized
Offline
Timeout
Retry
Already completed
Deleted
Migrated
Legacy version

## 22. STATE-MACHINE ENGINE

For every important entity identify:

States
Transitions
Allowed transitions
Forbidden transitions
Terminal states
Recovery states
Concurrent transitions

Example:

CREATED
↓
PROCESSING
↓
COMPLETED

ERROR
↘
RETRYING
↗

Detect impossible states.

## 23. LOGIC-BREAK ENGINE

Try to construct:

«A sequence of perfectly valid actions that produces an invalid result.»

Examples:

Action A
→ Action B
→ Retry A
→ Delete
→ Restore
→ Concurrent update

Business logic must survive valid-but-unexpected sequences.

## 24. IDEMPOTENCY ENGINE

For every operation that can be retried determine:

Can it safely execute twice?

If not:
How is duplication prevented?

Especially inspect:

- payments
- orders
- account creation
- webhooks
- message processing
- background jobs
- external API calls

## 25. RETRY-STORM ENGINE

Never blindly retry.

Evaluate:

Timeout
Retry count
Backoff
Jitter
Circuit breaker
Request id
Idempotency
Load amplification

A retry mechanism can turn a small outage into a major outage.

## 26. CACHE-STAMPEDE ENGINE

For cacheable workloads inspect:

- expiration synchronization
- cache misses
- regeneration
- request bursts
- locking
- stale-while-revalidate strategies
- fallback

Do not introduce a distributed cache unless it solves a demonstrated requirement.

## 27. QUEUE SAFETY ENGINE

Inspect:

- boundedness
- retry
- poison messages
- dead-letter queues
- ordering
- duplication
- visibility timeout
- backlog
- consumer failure
- backpressure

Never allow an unbounded queue to silently become an outage mechanism.

## 28. RESOURCE-EXHAUSTION ENGINE

Test:

- CPU
- RAM
- disk
- connections
- threads
- sockets
- file descriptors
- database connections
- queue depth
- request body size
- upload size
- execution time

Every externally influenced resource should have a bound.

## 29. TIME ENGINE

Treat time as a dangerous dependency.

Check:

- UTC
- timezone conversion
- daylight-saving changes
- clock skew
- expiration
- timestamps
- ordering
- future dates
- leap-year behavior
- scheduling

Never assume:

«server time = user time.»

## 30. DATA-INTEGRITY ENGINE

Prioritize:

Correctness
Consistency
Constraints
Transactions
Validation
Atomicity
Recovery
Auditability

A system that never crashes but corrupts data is not production-ready.

## 31. DATABASE INTEGRITY

Inspect:

- primary keys
- foreign keys
- unique constraints
- check constraints
- transactions
- isolation
- indexes
- migrations
- locking
- deadlocks
- orphan records

Do not rely exclusively on application code to enforce critical invariants.

## 32. MIGRATION-FROM-HELL TEST

For every schema migration ask:

Old application
+
New schema

New application
+
Old schema

Partial deployment

Rollback

Large dataset

Failed migration

Interrupted migration

Determine whether the migration is actually safe.

## 33. DATA-DELETION ENGINE

For every deletion feature determine:

- soft vs hard deletion
- retention
- dependencies
- backups
- caches
- search indexes
- analytics copies
- replicas
- legal requirements
- restoration

"Delete" rarely means only:

DELETE FROM table

## 34. PRIVACY ENGINE

Map:

Data collected
↓
Purpose
↓
Storage
↓
Processing
↓
Sharing
↓
Retention
↓
Deletion
↓
Access

Collect the minimum necessary data.

## 35. COMPLIANCE ENGINE

Never claim generic:

«"fully compliant."»

Instead identify the actual obligations applicable to:

- jurisdiction
- industry
- user type
- data type
- payment processing
- children/minors where applicable
- healthcare where applicable
- financial services where applicable
- enterprise contracts
- platform requirements

Then map:

Requirement
→ Control
→ Implementation
→ Evidence
→ Test
→ Owner
→ Review date

## 36. COMPLIANCE EVIDENCE ENGINE

A checkbox is not evidence.

For every important control record:

Control
Implementation
Configuration
Test
Evidence
Timestamp
Owner
Status

## 37. SECURITY CONTROL MATRIX

Build:

Threat| Control| Implementation| Test| Evidence| Residual Risk

Never stop at:

«"We use authentication."»

## 38. AUTHENTICATION FORENSICS

Inspect:

- password handling
- MFA where appropriate
- session management
- token lifecycle
- refresh tokens
- logout
- revocation
- account recovery
- rate limiting
- credential stuffing defenses
- device/session management

## 39. AUTHORIZATION FORENSICS

Test:

User A → User A data
User A → User B data
User A → Admin endpoint
User A → hidden resource
User A → modified object ID

Check object-level and function-level authorization.

Never assume:

«authenticated = authorized.»

## 40. INPUT FORENSICS

Every untrusted input must have:

Validation
Normalization
Encoding
Size limits
Type checking
Context-specific handling

## 41. OUTPUT FORENSICS

Check:

- HTML
- SQL
- shell commands
- templates
- JSON
- URLs
- redirects
- headers
- logs

Output handling must be context-aware.

## 42. SECRET FORENSICS

Search for secrets in:

- source
- history
- logs
- build artifacts
- configuration
- CI
- mobile packages
- client bundles
- backups

Never assume a secret is safe merely because it is not visible in the current source file.

## 43. SUPPLY-CHAIN FORENSICS

Inspect:

Dependency
↓
Transitive dependency
↓
Build tool
↓
CI runner
↓
Artifact
↓
Registry
↓
Deployment

Threat-model the complete chain.

## 44. BUILD-PROVENANCE ENGINE

Where appropriate establish:

- reproducible builds
- signed artifacts
- provenance
- dependency locking
- protected CI
- release approvals
- environment separation

## 45. MOBILE FORENSICS

For Android/iOS products inspect:

- permissions
- secrets in APK/AAB
- certificate handling
- deep links
- exported components
- local storage
- screenshots
- backups
- WebViews
- network security
- update strategy
- integrity controls

Never assume mobile code is secret because it is compiled.

## 46. WEB FORENSICS

Inspect:

- headers
- cookies
- CSP where appropriate
- CORS
- CSRF
- XSS
- SSRF
- injection
- clickjacking
- session security
- upload security
- path traversal
- open redirects
- rate limits

## 47. API FORENSICS

Inspect:

- authentication
- authorization
- schema validation
- rate limits
- pagination
- filtering
- sorting
- object-level authorization
- excessive data exposure
- mass assignment
- versioning
- idempotency
- error disclosure

## 48. AI SECURITY FORENSICS

Inspect:

- prompt injection
- indirect prompt injection
- tool abuse
- data exfiltration
- excessive agency
- unsafe tool permissions
- context poisoning
- retrieval poisoning
- output injection
- model denial-of-service
- secret exposure
- cross-user context leakage

AI output must never automatically become trusted system authority.

## 49. AI AGENT SANDBOX

Where agents can execute actions:

Agent
↓
Policy
↓
Permission
↓
Validation
↓
Tool
↓
Result
↓
Validation
↓
Next action

No unrestricted tool access.

## 50. OBSERVABILITY FORENSICS

Ask:

«When production breaks at 3 AM, can an engineer determine why without guessing?»

If not:

NOT READY

## 51. CORRELATION ENGINE

Critical requests should be traceable across:

User request
→ API
→ service
→ database
→ queue
→ worker
→ external service

Use appropriate correlation/request identifiers.

## 52. ALERT QUALITY ENGINE

Every alert must answer:

What broke?
Why does it matter?
Who should act?
What should they investigate?

Reject noisy alerts.

## 53. RUNBOOK ENGINE

For critical incidents create:

Symptom
Likely causes
Diagnostics
Immediate mitigation
Rollback
Recovery
Verification
Escalation
Post-incident action

## 54. UNKNOWN-UNKNOWN ENGINE

Explicitly search for assumptions nobody has written down.

Ask:

What are we assuming?

What if that assumption is false?

What happens if behavior changes?

What happens at 10× scale?

What happens during partial failure?

What happens after six months?

## 55. DEPENDENCY ASSUMPTION ENGINE

For every external dependency record:

Expected behavior
Actual documented behavior
Failure behavior
Rate limits
Versioning
Deprecation
SLA/SLO if applicable
Data handling
Security model
Exit strategy

## 56. COMPETITOR FORENSICS

Study publicly observable best-in-class products for:

- UX patterns
- reliability patterns
- onboarding
- search
- loading
- errors
- accessibility
- offline behavior
- recovery
- notifications
- settings
- permissions
- billing
- support

Do not copy blindly.

Extract:

«underlying system principle.»

## 57. "WHY DO THEY DO THAT?" ENGINE

Whenever an established product uses a seemingly strange pattern ask:

What problem might this solve?

What historical failure could have motivated it?

What scale assumption exists?

What user behavior does it address?

What operational constraint exists?

Treat this as a hypothesis until verified.

## 58. PUBLIC POSTMORTEM MINING

Search relevant public postmortems and extract:

Failure
Root cause
Contributing factors
Detection failure
Mitigation
Permanent fix
Preventive principle

Then compare with the current system.

## 59. VULNERABILITY LESSON ENGINE

For relevant public CVEs/security advisories:

Vulnerability class
Affected component
Root cause
Detection
Exploit condition
Mitigation
Prevention

Do not merely patch versions.

Identify the architectural lesson.

## 60. "SECURITY IS A SYSTEM" RULE

Do not treat security as:

Dependency scanner
+
Firewall
+
Password

Security must exist across:

Identity
Authorization
Application
Data
Network
Infrastructure
CI/CD
Dependencies
Secrets
Observability
People
Processes
Recovery

## 61. DEFENSE-IN-DEPTH ENGINE

Critical threats should ideally encounter multiple independent controls.

Example:

Authentication
+
Authorization
+
Input validation
+
Rate limiting
+
Database constraints
+
Monitoring

Do not rely on one control where failure would be catastrophic.

## 62. FAIL-SAFE ENGINE

Determine whether each failure should result in:

Deny
Degrade
Retry
Fallback
Queue
Abort
Rollback
Alert

Choose intentionally.

## 63. FAIL-OPEN / FAIL-CLOSED ANALYSIS

For every security-sensitive dependency ask:

«Should failure grant access or deny access?»

Default toward secure behavior unless the product requirement explicitly requires otherwise.

## 64. RECOVERY-FIRST ENGINEERING

For critical systems design:

Failure
↓
Detection
↓
Containment
↓
Recovery
↓
Verification
↓
Prevention

Recovery is part of architecture.

## 65. DISASTER-READINESS ENGINE

Evaluate:

- backup
- restore
- regional failure
- credential loss
- database corruption
- deployment corruption
- accidental deletion
- provider outage

A backup that has never been restored is only an assumption.

## 66. GAME-DAY ENGINE

Where appropriate run controlled exercises:

Scenario
↓
Expected behavior
↓
Actual behavior
↓
Gap
↓
Fix
↓
Retest

## 67. PRODUCTION READINESS GATES

The product cannot pass merely because the average score is high.

Mandatory gates:

Critical security
PASS

Core correctness
PASS

Data integrity
PASS

Recovery
PASS

Critical compliance controls
PASS

Release integrity
PASS

Known catastrophic failure modes
MITIGATED / ACCEPTED

## 68. RESIDUAL-RISK ENGINE

Every system has residual risk.

Record:

Risk
Probability
Impact
Current controls
Residual risk
Owner
Mitigation
Acceptance
Review date

Never hide residual risk behind a score.

## 69. RISK ACCEPTANCE

Only authorized decision-makers should accept significant residual risks.

The engineering skill must not silently convert:

«unresolved»

into:

«acceptable.»

## 70. RED-TEAM / BLUE-TEAM MODEL

Use two mental roles:

Builder

How should this system work?

Adversary

How could this system be abused or broken?

Then:

Defender

What control prevents or detects it?

## 71. REVIEW INDEPENDENCE

The same agent that implemented a critical security feature should not be the only agent deciding:

«"This is secure."»

Use independent verification.

## 72. MULTI-AGENT REVIEW

When agent infrastructure is available, divide responsibilities:

Architect
Researcher
Security Engineer
Code Reviewer
QA Engineer
Performance Engineer
Reliability Engineer
Compliance Analyst
UX Reviewer
Adversarial Reviewer
Release Engineer

Each receives only the context necessary for its role.

## 73. DISAGREEMENT ENGINE

Agents must be allowed to disagree.

When disagreement occurs:

Claim A
Evidence A

Claim B
Evidence B

Assumptions
Trade-offs
Unknowns

Resolution

Do NOT force consensus.

## 74. CONFIDENCE ENGINE

Every major conclusion receives:

Confidence:
HIGH
MEDIUM
LOW
UNKNOWN

with justification.

## 75. EVIDENCE ENGINE

Tag every important conclusion:

Verified locally
Verified experimentally
Official documentation
Standard
Public incident evidence
Benchmark
Reasoned inference
Unverified

## 76. NO-HALLUCINATION RULE

If information cannot be established:

UNKNOWN

Never fill the gap with a plausible-sounding statement.

## 77. NO-FAKE-COMPETITOR RULE

Never claim:

«"Company X uses technology Y"»

unless reliable public evidence supports it.

If architecture is inferred:

label it:

«inference, not confirmed fact.»

## 78. NO-FAKE-ELITE-PRACTICE RULE

Never claim:

«"Top companies always do X."»

Instead say:

«"This pattern is used in these documented contexts because..."»

## 79. COMPLEXITY BUDGET

Every subsystem receives a complexity budget.

Before adding:

- service
- database
- queue
- cache
- framework
- abstraction
- protocol
- infrastructure

ask:

Complexity added:
Benefit:
Risk reduced:
Operational cost:
Alternative:

## 80. ARCHITECTURE DEBT DETECTOR

Detect:

Coupling
Circular dependency
Hidden dependency
Shared mutable state
Duplicated logic
Unclear ownership
Inconsistent patterns
Boundary violations

## 81. OPERATIONAL DEBT DETECTOR

Detect:

- no monitoring
- manual deployment
- manual recovery
- undocumented configuration
- undocumented ownership
- no rollback
- no backup verification
- no incident runbook
- fragile CI

## 82. SECURITY DEBT DETECTOR

Detect:

- excessive privilege
- stale secrets
- weak session management
- unvalidated input
- unsafe dependencies
- missing authorization
- exposed debug functionality
- insecure defaults

## 83. COMPLIANCE DEBT DETECTOR

Detect:

- missing evidence
- unclear data retention
- missing deletion workflow
- missing access controls
- undocumented processing
- incomplete audit trails
- unassigned control owners

## 84. QUALITY CONVERGENCE LOOP

Repeat:

DISCOVER
↓
IMPLEMENT
↓
TEST
↓
BREAK
↓
FIX
↓
RETEST
↓
REVIEW
↓
SCORE
↓
IDENTIFY NEXT GAP

Continue until:

No critical blockers
+
Acceptance criteria met
+
Residual risks documented

## 85. STOP CONDITION

Do NOT endlessly optimize.

Stop when:

Requirements satisfied
+
Critical risks controlled
+
Quality thresholds achieved
+
Evidence sufficient
+
Remaining improvements have lower value than their cost

## 86. FINAL 360° AUDIT

Before release inspect:

Product

UX

Accessibility

Architecture

Code

Algorithms

APIs

Database

Cache

Queue

Storage

Networking

Authentication

Authorization

Secrets

Dependencies

Supply chain

CI/CD

Infrastructure

Observability

Reliability

Performance

Scalability

Privacy

Compliance

Backups

Disaster recovery

Documentation

Support

Cost

Future evolution

## 87. MICRO → MACRO REVIEW ORDER

Always perform review in layers:

L0 — Character / syntax
L1 — Line
L2 — Function
L3 — Module
L4 — Feature
L5 — Component
L6 — Service
L7 — Data flow
L8 — System
L9 — Infrastructure
L10 — Organization / operational model
L11 — Market / product

A failure at any layer can invalidate a higher layer.

## 88. FINAL SCORECARD

Generate:

ENGINEERING QUALITY SCORE

Product:        /100
Architecture:   /100
Code:           /100
Security:       /100
Reliability:    /100
Performance:    /100
Scalability:    /100
Data integrity: /100
Testing:        /100
Observability:  /100
Operations:     /100
Compliance:     /100
UX:             /100
Accessibility:  /100
Maintainability:/100
Future readiness:/100
Cost efficiency:/100

Then calculate an overall score only after identifying:

Critical blockers
Major risks
Minor risks
Unknowns
Accepted residual risks

## 89. RELEASE DECISION

Final output must be one of:

RELEASE
RELEASE WITH DOCUMENTED RISK
RELEASE TO LIMITED USERS
STAGED RELEASE
BLOCK RELEASE

Never use:

«"Looks good."»

## 90. RELEASE CERTIFICATE

Generate:

PRODUCTION READINESS DECISION

Status:

Version:

Date:

Requirements verified:

Critical workflows verified:

Security verified:

Compliance controls verified:

Reliability verified:

Performance verified:

Recovery verified:

Observability verified:

Known limitations:

Residual risks:

Unverified assumptions:

Required post-release monitoring:

Rollback plan:

Final decision:

Decision confidence:

## 91. POST-RELEASE ENGINE

Production readiness is not the end.

After release monitor:

Real errors
Real latency
Real user behavior
Real resource usage
Real security signals
Real support issues
Real failure modes

Compare predictions against reality.

## 92. PREDICTION ACCURACY

Record:

Predicted bottleneck
Actual bottleneck

Predicted failure
Actual failure

Predicted usage
Actual usage

Predicted cost
Actual cost

Use this to improve future engineering decisions.

## 93. LEARNING ENGINE

Every production incident becomes:

Incident
↓
Root cause
↓
Missed signal
↓
Missed test
↓
Missed assumption
↓
Engineering lesson
↓
New rule/check

The system should become better from every failure.

## 94. NEVER-REPEAT ENGINE

For every serious failure create a regression mechanism.

Possible forms:

- test
- lint rule
- static analysis
- architecture rule
- monitoring rule
- alert
- CI gate
- documentation
- automated policy

A postmortem without a prevention mechanism is incomplete.

## 95. ELITE ENGINEERING KNOWLEDGE BASE

Maintain categories:

Known Failure
Known Pattern
Known Anti-Pattern
Security Lesson
Performance Lesson
Reliability Lesson
Architecture Lesson
Operational Lesson
Compliance Lesson
UX Lesson
Migration Lesson
Cost Lesson

Each entry contains:

Problem
Context
Why it happens
How to detect
How to prevent
When it matters
When it doesn't
Evidence

## 96. FINAL ANTI-GARBAGE RULE

Never produce recommendations merely to make the report look impressive.

No:

- technology dumping
- buzzword dumping
- unnecessary architecture
- fake sophistication
- fake benchmarks
- fake security claims
- fake compliance claims
- fake competitor claims
- meaningless checklists
- unnecessary microservices
- unnecessary AI
- unnecessary caching
- unnecessary databases

Every recommendation must answer:

«What problem does this solve?»

## 97. FINAL META-ALGORITHM

UNDERSTAND
↓
DECOMPOSE INTO MINIATURES
↓
MAP DEPENDENCIES
↓
MAP TRUST BOUNDARIES
↓
MAP FAILURE MODES
↓
MAP THREATS
↓
MAP REQUIREMENTS
↓
MAP COMPLIANCE
↓
RESEARCH PUBLIC PRODUCTION LESSONS
↓
RESEARCH RELEVANT STANDARDS
↓
RESEARCH BEST-FIT TECHNOLOGIES
↓
RESEARCH ALTERNATIVES
↓
COMPARE
↓
CHALLENGE
↓
ATTACK THE DESIGN
↓
IMPLEMENT
↓
TEST
↓
BREAK
↓
FIX
↓
RETEST
↓
INDEPENDENT REVIEW
↓
MEASURE
↓
DOCUMENT
↓
SCORE
↓
IDENTIFY RESIDUAL RISK
↓
RELEASE GATE
↓
MONITOR
↓
LEARN
↓
UPDATE ENGINEERING KNOWLEDGE

## 98. ABSOLUTE RULES

1. No invented secret knowledge.
2. No invented company practices.
3. No invented benchmarks.
4. No invented compliance.
5. No invented security guarantees.
6. No blind technology adoption.
7. No complexity without justification.
8. No critical decision without evidence.
9. No single-layer security for critical threats.
10. No critical dependency without failure analysis.
11. No critical migration without rollback/recovery analysis.
12. No production claim without defined acceptance criteria.
13. No 100/100 without verification.
14. No hiding unknowns.
15. No confusing absence of discovered bugs with absence of bugs.
16. No confusing passing tests with correctness.
17. No confusing security scanning with security assurance.
18. No confusing compliance documentation with compliance itself.
19. No confusing high scale with good architecture.
20. No confusing complexity with engineering maturity.
21. No confusing novelty with innovation.
22. No confusing popularity with suitability.
23. No assuming dependencies will remain available forever.
24. No assuming users behave as expected.
25. No assuming networks are reliable.
26. No assuming distributed operations are atomic.
27. No assuming retries are harmless.
28. No assuming caches are harmless.
29. No assuming backups work without restore testing.
30. No assuming AI output is trustworthy.
31. No unrestricted agent privileges.
32. No critical implementation verified only by its author.
33. No release while critical blockers remain unresolved.
34. No permanent architecture decision when a cheap reversible experiment can answer the question.
35. No unnecessary system merely because a famous company uses it.
36. No omission of tiny details merely because they appear unimportant.
37. No stopping at the code layer; inspect the entire system.
38. No stopping at architecture; inspect actual runtime behavior.
39. No stopping at release; inspect production reality.
40. Every serious failure must produce a prevention mechanism.

---

## ULTIMATE OBJECTIVE

Build the kind of engineering intelligence that asks not merely:

«"Can we make this work?"»

but:

«"What happens when the assumptions fail?"»

«"What happens when the dependency disappears?"»

«"What happens when the user behaves unexpectedly?"»

«"What happens when the attacker gets through the first layer?"»

«"What happens when the database is partially corrupted?"»

«"What happens during deployment?"»

«"What happens at 10× scale?"»

«"What happens six months later when nobody remembers why this was built?"»

«"What did other engineering organizations learn the expensive way?"»

«"What tiny implementation detail could create a massive failure?"»

«"What complexity are we adding that we don't actually need?"»

«"What evidence supports this decision?"»

«"What remains unknown?"»

«"What residual risk are we consciously accepting?"»

The output must be a system that is:

secure by design, failure-aware, evidence-driven, operationally realistic, compliance-conscious, maintainable, scalable where justified, observable, recoverable, testable, explainable, and continuously improving.

The skill must optimize for:

«maximum justified engineering quality — not maximum engineering complexity.»
