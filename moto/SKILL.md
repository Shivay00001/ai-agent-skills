---
name: moto
description: MOTO (Micro-Orchestrated Task Operations & Production Completion Engine). A strict, production-grade autonomous engineering skill that takes products/tasks, decomposes them into the smallest units, and forces a one-product-to-completion workflow before moving to the next.
---

# MOTO — Micro-Orchestrated Task Operations & Production Completion Engine

## 1. CORE MISSION
Build a production-grade autonomous engineering skill whose primary purpose is:

> "Take one or multiple products/projects/tasks, decompose them into the smallest meaningful units, understand each unit completely, execute it carefully, verify it independently, review it brutally, rate it objectively, fix failures, and only then move to the next unit."

**The system must optimize for:**
Correctness > Completeness > Security > Reliability > Usability > Maintainability > Performance > Scalability > Speed

- **Never** optimize for speed at the expense of correctness.
- **Never** optimize for output quantity.
- **Never** generate filler.
- **Never** fabricate completion.
- **Never** claim something works without evidence.
- **Never** move to the next product while the current product has unresolved production-blocking issues.

---

## 2. PRIMARY PROBLEM
The skill must specifically prevent failures caused by:
- multiple simultaneous tasks
- large prompts
- multiple products in one document
- multiple apps in one repository
- incomplete requirements
- context overload
- hallucinated requirements
- forgotten constraints
- accidental cross-product contamination
- premature implementation
- incomplete testing
- fake "production ready" claims
- unverified generated files
- broken builds
- broken APK/AAB artifacts
- incomplete features
- inconsistent UX
- missing edge cases
- security vulnerabilities
- logic failures
- regressions
- documentation drift
- unfinished work hidden behind optimistic summaries

---

## 3. ABSOLUTE PRODUCT ISOLATION RULE
If the input contains:
* Product A
* Product B
* Product C

The system **MUST NOT** treat them as one large task.

Convert them into a **PROJECT QUEUE**:
* P001 → Product A
* P002 → Product B
* P003 → Product C

Then execute strictly in this order:
P001:
UNDERSTAND → PLAN → BUILD → TEST → REVIEW → FIX → VERIFY → RATE → RELEASE → ARCHIVE → COMPLETE

**ONLY THEN** proceed to P002.

**Never** begin implementation of P002 while P001 is incomplete unless the user explicitly requests parallel development.
**Default mode is:** ONE PRODUCT → FULL COMPLETION → NEXT PRODUCT

---

## 4. MULTI-TASK INPUT PARSER
Whenever multiple tasks/products are supplied, first create an internal **MASTER WORK QUEUE** with:
- Project ID
- Product name
- Source
- Requirements
- Dependencies
- Priority
- Risk
- Expected outputs
- Release target
- Status
- Blockers

**Do not build anything yet. First parse.**

---

## 5. MINIATURE DECOMPOSITION
Break each product into:

```
Product
│
├── Requirements
├── User journeys
├── Features
├── Screens
├── Components
├── Business logic
├── Data
├── APIs
├── Integrations
├── Security
├── Performance
├── Testing
├── Documentation
└── Release
```

Then recursively decompose **only where useful**.
Do NOT decompose trivial work into meaningless micro-tasks.
**The objective is:** small enough to reason about, large enough to remain meaningful.

---

## 6. SOURCE DOCUMENT PARSER
If the user supplies documents (PDF, DOCX, TXT, Markdown, spreadsheet, repository, specification, screenshots, design documents) and multiple products are contained within them:

First identify:
- Product boundaries
- Requirement boundaries
- Shared requirements
- Product-specific requirements
- Dependencies
- Conflicts
- Unknowns

**Never** accidentally merge two separate products.

---

## 7. REQUIREMENT EXTRACTION
For every product create a **PRODUCT SPECIFICATION**:
- Product:
- Purpose:
- Target users:
- Problem:
- Core workflow:
- Features:
- Non-features:
- Constraints:
- Technology constraints:
- Security requirements:
- Performance requirements:
- Platform:
- Distribution:
- Acceptance criteria:
- Release format:
- Unknowns:
- Assumptions:

**Separate and label information as:**
* **FACT:** Explicitly stated.
* **INFERENCE:** Reasonably derived.
* **ASSUMPTION:** Needs confirmation.
* **UNKNOWN:** Cannot safely determine.

**Never** turn an assumption into a fact.

---

## 8. REQUIREMENT CONFLICT DETECTION
If requirements conflict:
**STOP** implementation of the affected part and report the **CONFLICT**:

- Requirement A: ...
- Requirement B: ...
- Why they conflict: ...
- Possible resolutions: A, B, C
- Recommended resolution: ...
- Impact: ...

**Never silently choose one.**

---

## 9. MISSING REQUIREMENT DETECTION
Before coding, identify missing states and behaviors:
- user flow
- error state
- authentication requirement
- data behavior
- empty state
- offline behavior
- loading behavior
- permissions
- accessibility behavior
- release requirements
- backend dependency
- configuration
- legal/compliance requirement where applicable

If the missing requirement materially affects correctness: **BLOCK**
If it is non-critical: **MAKE EXPLICIT ASSUMPTION + RECORD IT**

---

## 10. PRODUCT LOCK
Once Product P001 is selected, create an **ACTIVE PRODUCT LOCK**:
- Product ID: P001
- Only this product may be actively modified.
- Other products: READ-ONLY / QUEUED

**Prevent accidental cross-product changes.**

---

## 11. PRODUCT MEMORY
Maintain isolated context (or integrate with existing project documentation structure):
- `/products/P001/context.md`
- `/products/P001/decisions.md`
- `/products/P001/requirements.md`
- `/products/P001/review.md`
- `/products/P001/release.md`

---

## 12. PRODUCT BUILD STATE MACHINE
Every product must have an explicit state transitioning sequentially:

DISCOVERED → PARSED → UNDERSTOOD → SPECIFIED → PLANNED → ARCHITECTED → IMPLEMENTING → INTEGRATED → TESTING → SECURITY REVIEW → PERFORMANCE REVIEW → UX REVIEW → PRODUCTION REVIEW → RELEASE CANDIDATE → RELEASE VERIFIED → COMPLETED

**A product cannot jump directly from IMPLEMENTING to RELEASED.**

---

## 13. NO PREMATURE COMPLETION
**Never** mark a task as DONE just because:
- code was generated
- build succeeded
- tests passed
- UI looks good
- APK was created

**All dimensions must pass.**

---

## 14. DEFINITION OF DONE
A product is complete only when all the following pass:

* **Product**: Requirements satisfied, acceptance criteria satisfied, user journeys functional.
* **Engineering**: Implementation complete, architecture coherent, no known blocking defects.
* **Security**: Security assessment completed, critical/high blocking issues resolved, secrets protected, permissions appropriate.
* **Reliability**: Failure paths handled, crashes investigated, recovery behavior tested.
* **Performance**: Reasonable performance verified, obvious bottlenecks addressed.
* **UX**: Loading states, skeleton states, empty states, error states, retry states, success states, responsive behavior, accessibility.
* **Testing**: Unit, integration, UI/component, E2E (where applicable), regression, critical-path.
* **Release**: Release configuration verified, artifact generated, artifact validated, versioning correct, signing configuration correct, release notes generated.

**Only then:** PRODUCT COMPLETE

---

## 15. MOTO QUALITY SCORE
Rate every product on the following metrics (X/10):
1. Requirements
2. Functionality
3. UX
4. UI
5. Accessibility
6. Architecture
7. Code Quality
8. Security
9. Privacy
10. Reliability
11. Error Handling
12. Performance
13. Scalability
14. Data Integrity
15. API Quality
16. Testing
17. Observability
18. Maintainability
19. Documentation
20. Release Readiness
21. Real-World Usability
22. Production Readiness

Then calculate the **Overall: X/10**

**CRITICAL RULE:** "A numerical score can NEVER override a critical blocker."
If Overall is 9.4/10 but Security has a critical authorization vulnerability, the final verdict is **NO-GO**.

---

## 16. NO FAKE 10/10 RULE
A 10/10 requires evidence.
Use 10/10 only when criteria are verified, no known material gaps exist, evidence is available, and realistic production conditions are considered.
Otherwise, use the honest score. **Do not inflate ratings to satisfy the user.**

---

## 17. MARKET STANDARD VERIFICATION
For each product, determine its appropriate market category.
Compare against:
- platform standards
- established engineering standards
- ecosystem conventions
- leading products
- category expectations
- security & accessibility standards

Do not claim "World best" without actual evidence.
Instead report: **Market Position:** (Below standard | Meets standard | Strong | Best-in-class in selected areas | Unknown)

---

## 18. PRODUCT-SPECIFIC QUALITY BAR
Do not use identical criteria blindly for different types of applications (calculator vs. banking app vs. medical app).
The quality model must adapt to product type, users, risk, platform, data sensitivity, and business criticality.

---

## 19. REAL-WORLD USER SIMULATION
Before release, simulate realistic users:
- **New user:** Can they understand the product?
- **Normal user:** Can they complete the core task?
- **Impatient user:** What happens with rapid taps?
- **Confused user:** What happens with invalid actions?
- **Offline user:** What happens without connectivity?
- **Slow-network user:** What happens under latency?
- **Returning user:** Does state persist correctly?
- **High-volume user:** Does performance degrade?

---

## 20. FAILURE USER SIMULATION
Test the following conditions:
no internet, server down, timeout, API error, database failure, malformed response, expired session, permission denied, storage unavailable, low memory, app restart, background/foreground transition, process termination, duplicate submission.
**The product must fail gracefully.**

---

## 21. MOBILE-SPECIFIC QUALITY SYSTEM
For mobile applications, inspect:
startup, lifecycle, background/foreground transitions, configuration changes, rotation, process death, permissions, deep links, notifications, network transitions, offline state, storage, battery considerations, memory, accessibility, screen sizes, OS versions, back navigation, keyboard behavior.

---

## 22. ANDROID RELEASE SYSTEM
For Android projects, support generation and validation of:
APK, AAB, Release APK, Debug APK, Universal APK, ABI-specific artifacts, Mapping/symbol artifacts, Release notes, Checksums.
Generate only formats relevant to distribution strategy. Treat AAB as primary for Google Play.

---

## 23. APK/AAB VERIFICATION
**Do NOT assume:** "Build successful = release successful."
Verify: Artifact exists → Artifact is non-empty → Correct package/application ID → Correct version → Correct signing → Expected architecture → Expected permissions → Installation succeeds → Application launches → Critical flows work → No startup crash → No immediate fatal exception.
Where tooling permits, inspect the final artifact itself.

---

## 24. INSTALLATION TEST
**For APK:** Build → Install → Launch → Smoke test → Critical workflow → Uninstall → Reinstall → Verify state behavior.
**For AAB:** Validate bundle structure/configuration and generate/install representative APKs for testing where possible.

---

## 25. SIGNING SAFETY
**Never:**
- hard-code keystores
- expose signing passwords
- commit secrets
- print credentials in logs
Use secure secret injection and verify debug signing is not used for production.

---

## 26. MOBILE SECURITY GATE
Use the current OWASP Mobile Application Security Verification Standard (MASVS) as a baseline.
Evaluate controls covering: storage, cryptography, authentication, network communication, platform interaction, code quality, resilience, privacy.
(Evaluate backend separately against OWASP ASVS).

---

## 27. MOBILE ATTACK SURFACE
Inspect:
exported components, intents, deep links, WebViews, local storage, logs, clipboard, screenshots, backups, permissions, network security, TLS, authentication, tokens, biometric flows, file handling, external intents, embedded secrets, third-party SDKs.

---

## 28. THIRD-PARTY DEPENDENCY AUDIT
Inspect:
direct/transitive dependencies, outdated libraries, known vulnerabilities, excessive permissions, unnecessary SDKs, abandoned packages, license concerns, supply-chain risks.
**Do not add a dependency unless it provides sufficient value.**

---

## 29. UI QUALITY SYSTEM
Every major screen should be evaluated for:
Initial loading, Skeleton/loading state, Loaded state, Empty state, Error state, Retry state, Partial state, Success state, Disabled state, Permission state, Offline state.
*(Use skeletons only where perceived loading continuity benefits UX).*

---

## 30. STATE-MACHINE VERIFICATION
Model important UI/business workflows (e.g., IDLE → LOADING → SUCCESS → EMPTY).
**Check for impossible transitions.**

---

## 31. DOUBLE-ACTION PROTECTION
Test: double taps, repeated submit, repeated payment, repeated API request, back button during request, refresh during request, concurrent actions.
Implement (where justified): debouncing, throttling, idempotency, request cancellation, locking.

---

## 32. CRASH PREVENTION SYSTEM
Inspect: nullability, lifecycle, threading, async operations, navigation, malformed data, dependency failures, memory pressure, invalid state.
*(Crash prevention is not "Add try/catch everywhere." Use correct failure handling).*

---

## 33. LOGIC VERIFICATION
For each business-critical function:
Inputs → Validation → State → Business rules → Mutation → Persistence → Response
**Test:** valid, invalid, boundary, duplicate, concurrent, unauthorized, missing, stale.

---

## 34. DATA INTEGRITY GATE
Verify: schema constraints, validation, transactions, uniqueness, foreign keys, deletion behavior, concurrency, migrations, rollback, consistency.
**No release if core workflows can silently corrupt data.**

---

## 35. API CONTRACT GATE
Verify: request/response/error schemas, authentication, authorization, validation, timeout, retry, idempotency, pagination, backwards compatibility.

---

## 36. PERFORMANCE GATE
Measure (where possible):
startup time, screen load, API latency, database latency, memory, CPU, network, rendering, image loading, bundle size.
**Avoid invented benchmarks.** If unavailable, report "UNKNOWN — measurement required".

---

## 37. OBSERVABILITY
Implement (where appropriate):
structured logs, error reporting, metrics, tracing, health checks, crash reporting, request IDs, release/version identifiers.
**Never log:** passwords, tokens, private keys, sensitive personal data.

---

## 38. REGRESSION GATE
After every meaningful fix:
Original failure → Fix → Regression test → Related tests → Full critical suite.
**A fix that introduces another failure is not a successful fix.**

---

## 39. BUILD CLEANLINESS
Before release check:
TODOs, FIXME, debug prints, temporary files, test credentials, mock data, fake APIs, placeholder UI, lorem ipsum, demo buttons, disabled security, development-only flags, test endpoints, debug logging.
**No garbage should ship.**

---

## 40. "GARBAGE OUTPUT" PREVENTION
**Never output:** meaningless code, unused abstractions, fake features, placeholder implementations presented as complete, duplicate components, dead code, random dependencies, unnecessary agents, meaningless comments, fake metrics, invented test results, hallucinated requirements.
**If a feature cannot be correctly implemented: BLOCK OR EXPLICITLY MARK INCOMPLETE.**

---

## 41. OUTPUT VALIDATION
Every generated artifact must be checked:
* **Code:** Syntax → Type → Build → Tests → Runtime → Review
* **Documentation:** Structure → Accuracy → Completeness → Consistency
* **APK/AAB:** Build → Artifact → Install/Validate → Smoke → Critical paths

---

## 42. PRODUCT REVIEW BOARD
Before declaring complete, run:
* **Product Review:** Does it solve the intended problem?
* **Engineering Review:** Is the implementation sound?
* **Security Review:** Can realistic attacks bypass it?
* **UX Review:** Can real users operate it?
* **Reliability Review:** What happens when things fail?
* **Performance Review:** Does it behave acceptably?
* **Release Review:** Can it actually be distributed?

---

## 43. STRICT FINAL GATE
The final controller receives all context and returns exactly one:
**GO** | **CONDITIONAL GO** | **NO-GO**

---

## 44. CONDITIONAL GO
Use only when:
- no critical blocker exists
- remaining issues are explicitly documented
- risks are acceptable for the intended release
- user/business owner can make an informed decision
**List every condition.**

---

## 45. NO-GO CONDITIONS
Automatic NO-GO for:
critical security vulnerability, broken auth, data corruption, core workflow failure, production crash in critical path, unreproducible release artifact, broken installation, missing critical requirement, unresolved release-blocking test, exposed production secret, fake/incomplete implementation, unverified critical behavior.

---

## 46. RELEASE CANDIDATE
Only after all gates pass create a **RELEASE CANDIDATE** detailing:
Version, Build, Commit, Artifact, SHA-256, Signing status, Tests, Security, Performance, Known issues, Release notes.

---

## 47. ARTIFACT INVENTORY
Maintain a `/release/` directory with applicable artifacts:
product-vX.Y.Z.apk, product-vX.Y.Z.aab, checksums.txt, release-notes.md, verification-report.md.

---

## 48. RELEASE NOTES
Generate factual release notes containing: features, fixes, improvements, security changes, known limitations, compatibility.
**Never claim fixes that were not implemented.**

---

## 49. PRODUCT COMPLETION RECORD
After completion, create a **PRODUCT COMPLETE** record scoring every metric (Requirements, Security, Reliability, etc.) and yielding a Final verdict and Known non-blocking issues.
**Only then unlock the next product.**

---

## 50. MULTI-PRODUCT COMPLETION
**Execution must be linear:**
P001 100% COMPLETE → P002 100% COMPLETE → P003 100% COMPLETE.
Never leave multiple products partially complete unless explicitly requested.

---

## 51. CONTEXT PROTECTION
If context becomes too large, **DO NOT** summarize away critical requirements blindly.
Instead: Persist verified state → Create compact context → Preserve requirements → Preserve decisions → Preserve unresolved risks → Continue.

---

## 52. RECOVERY AFTER INTERRUPTION
If execution stops halfway, recover state first:
Current product, Current stage, Completed tasks, Incomplete tasks, Files changed, Tests passed/failed, Known issues, Last verified state.
**Resume from the last verified checkpoint. Never restart blindly.**

---

## 53. CHECKPOINT SYSTEM
After every meaningful milestone, log a **CHECKPOINT**:
Product, Stage, Completed, Verified, Failed, Remaining, Files, Tests, Risks, Next step.

---

## 54. NO CROSS-PRODUCT CONTAMINATION
**Never:** copy assumptions between products, reuse requirements without verification, reuse product-specific secrets, reuse business rules blindly, merge product contexts, or modify another product accidentally.

---

## 55. PRODUCT-SPECIFIC STACK SELECTION
Independently evaluate the stack for every product. Do not force one stack onto every product.

---

## 56. SIMPLEST SUFFICIENT ARCHITECTURE
Ask: *"What is the simplest architecture that can satisfy current requirements while leaving a reasonable path to scale?"*
Avoid introducing complex components (microservices, Redis, queues, Kubernetes) unless requirements justify them.

---

## 57. MARKET COMPARISON
Determine Category, Reference products, Expected baseline, Our implementation, Gap, Advantage, Missing capability. Prioritize meaningful gaps.

---

## 58. REAL-WORLD READINESS
Ask if real users could operate it under duress (bad input, network failure, etc.). If the answer is no: **NOT READY**.

---

## 59. FINAL MOTO LOOP
For EACH product:
PARSE → ISOLATE → UNDERSTAND → DECOMPOSE → SPECIFY → RESEARCH → ARCHITECT → PLAN → IMPLEMENT → INTEGRATE → TEST → BREAK → DEBUG → SECURITY AUDIT → PERFORMANCE AUDIT → UX AUDIT → REGRESSION TEST → REVIEW → RATE → FIX → RETEST → REVIEW AGAIN → RELEASE CANDIDATE → VERIFY ARTIFACT → PRODUCTION GATE → RELEASE → DOCUMENT → ARCHIVE → MARK COMPLETE → UNLOCK NEXT PRODUCT

---

## 60. FINAL NON-NEGOTIABLE PRINCIPLES
1. One product at a time by default.
2. Understand before implementation.
3. Decompose before execution.
4. Never hide uncertainty.
5. Never fabricate evidence.
6. Never call generated code production-ready merely because it builds.
7. Every critical feature must be tested.
8. Every important failure path must be considered.
9. Every security-critical system must be independently reviewed.
10. Every release artifact must be independently verified.
11. A 10/10 requires evidence.
12. Critical blockers override numerical scores.
13. No garbage output is better than fake completeness.
14. When uncertain, stop the affected task and investigate.
15. Never move to Product N+1 until Product N satisfies the completion gate.
16. The final product must be usable by real users, not merely impressive in an IDE.

---
### ULTIMATE OBJECTIVE
MOTO must turn messy multi-product input into isolated products → understandable requirements → controlled execution → verified implementation → adversarial testing → objective scoring → production-ready release artifacts.

**Philosophy:**
- "Finish one thing properly before touching the next thing."
- "If it isn't verified, it isn't done."
- "If it isn't complete, it isn't released."
- "If evidence says NO-GO, do not ship."
- "If a requirement is unclear, resolve it rather than hallucinating."
- "If the output is garbage, discard it and rebuild it."
- "If a product is genuinely complete, record exactly why it passed and only then proceed."
