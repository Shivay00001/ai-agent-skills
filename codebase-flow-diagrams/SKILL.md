---
name: codebase-flow-diagrams
description: >-
  Generates comprehensive flow diagram markdown (.md) files for any codebase to
  visually document and explain code, programs, features, systems, components,
  system architecture, design patterns, data flows, and more. Also teaches and
  explains every part of the codebase in deeply detailed, easy-to-understand
  language with real-life examples and analogies. Use this skill whenever the
  user asks to generate flow diagrams, architecture diagrams, system maps,
  component diagrams, visual documentation, or to explain/teach a codebase.
  Also activate when the user says "generate flows", "map the codebase",
  "diagram the system", "visualize architecture", "create flow docs",
  "explain this codebase", "teach me this code", or "how does this work".
---

# Codebase Flow Diagram Generator & Deep Explainer

## ROLE

You are a System Architect + Visual Documentation Engineer + Master Code
Teacher. Your job is to analyze any codebase and produce TWO comprehensive
documents:

1. **`FLOW_DIAGRAMS.md`** — Visual flow diagrams making the system
   understandable at every level (architecture → components → functions).
2. **`CODEBASE_EXPLAINED.md`** — A deeply detailed, beginner-friendly
   explanation of the entire codebase using plain language, real-life
   analogies, and progressive learning layers.

Together, these documents turn any project into a self-teaching system that
a complete beginner can read and understand, while still providing depth
that experienced developers find valuable.

---

## 1. ACTIVATION & SCOPE

### When to Activate
- User asks to generate flow diagrams for a project
- User asks to "map", "visualize", or "diagram" a codebase
- A new project is opened and the user wants understanding docs
- User requests architecture documentation with visual flows

### What to Produce
Generate a single `FLOW_DIAGRAMS.md` file (or split into multiple if the
codebase is very large) placed at the project root. This file contains all
diagrams using **Mermaid** syntax for maximum portability and rendering support.

---

## 2. ANALYSIS WORKFLOW

Follow this sequence rigorously before generating any diagrams:

### Phase 1 — Discovery
1. **Scan the project structure** — List all directories and files to understand
   the project layout, framework, and language(s).
2. **Identify the tech stack** — Detect frameworks, libraries, build tools,
   runtime environments, databases, and external services.
3. **Identify entry points** — Find `main()`, `index.*`, route definitions,
   CLI entry points, event handlers, serverless functions, etc.
4. **Identify configuration** — Read config files, environment variables,
   dependency manifests (`package.json`, `requirements.txt`, `go.mod`, etc.).

### Phase 2 — Structural Analysis
1. **Map modules/packages** — Identify logical groupings (domains, features,
   layers, services).
2. **Map dependencies** — Trace imports, requires, and dependency injection
   to understand which modules depend on which.
3. **Map data models** — Identify entities, schemas, database tables, DTOs,
   and their relationships.
4. **Map API surface** — Identify routes, endpoints, GraphQL resolvers, gRPC
   services, WebSocket handlers, CLI commands.

### Phase 3 — Behavioral Analysis
1. **Trace request flows** — Follow a request from entry to response through
   all layers (routing → middleware → controller → service → repository → DB).
2. **Trace data flows** — Follow data from creation through transformation,
   storage, retrieval, and display.
3. **Trace event flows** — Map event emitters, listeners, pub/sub, message
   queues, webhooks.
4. **Trace error flows** — Map error handling chains, fallbacks, retries,
   circuit breakers.
5. **Trace auth flows** — Map authentication and authorization paths.

---

## 3. DIAGRAM CATEGORIES

Generate diagrams for ALL applicable categories below. Skip categories that
are genuinely not present in the codebase. Never fabricate flows that don't
exist.

### 3.1 System Architecture Overview
A bird's-eye view of the entire system showing all major components and their
relationships.

```
graph TB
    subgraph "Frontend"
        ...
    end
    subgraph "Backend"
        ...
    end
    subgraph "Data Layer"
        ...
    end
    subgraph "External Services"
        ...
    end
```

### 3.2 Directory & Module Structure
A tree diagram showing the project's organizational structure with purpose
annotations.

### 3.3 Component Dependency Graph
Shows which components/modules depend on which, revealing coupling and
dependency direction.

```
graph LR
    ComponentA --> ComponentB
    ComponentA --> ComponentC
    ComponentB --> SharedLib
    ComponentC --> SharedLib
```

### 3.4 Request/Response Flow
For each major API endpoint or user action, trace the complete lifecycle:

```
sequenceDiagram
    participant User
    participant Frontend
    participant API Gateway
    participant Auth
    participant Service
    participant Database
    User->>Frontend: Action
    Frontend->>API Gateway: HTTP Request
    API Gateway->>Auth: Validate Token
    Auth-->>API Gateway: Valid
    API Gateway->>Service: Process
    Service->>Database: Query
    Database-->>Service: Result
    Service-->>API Gateway: Response
    API Gateway-->>Frontend: HTTP Response
    Frontend-->>User: Updated UI
```

### 3.5 Data Flow Diagram
Shows how data moves through the system — from input to storage to output.

```
flowchart LR
    Input["User Input"] --> Validate["Validation Layer"]
    Validate --> Transform["Transform/Map"]
    Transform --> Store["Database"]
    Store --> Cache["Cache Layer"]
    Cache --> API["API Response"]
    API --> Render["UI Render"]
```

### 3.6 State Machine Diagrams
For entities with lifecycle states (orders, users, payments, deployments, etc.):

```
stateDiagram-v2
    [*] --> Draft
    Draft --> Pending: Submit
    Pending --> Approved: Approve
    Pending --> Rejected: Reject
    Approved --> Active: Activate
    Active --> Completed: Complete
    Completed --> [*]
```

### 3.7 Database / Entity Relationship Diagram
Map all entities and their relationships:

```
erDiagram
    USER ||--o{ ORDER : places
    ORDER ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : "is ordered in"
```

### 3.8 Authentication & Authorization Flow
Map the complete auth lifecycle:

```
flowchart TD
    Request --> CheckToken{Token Present?}
    CheckToken -->|No| Login["Login Page"]
    CheckToken -->|Yes| ValidateToken{Valid?}
    ValidateToken -->|No| RefreshToken{Refresh?}
    ValidateToken -->|Yes| CheckPermissions{Authorized?}
    CheckPermissions -->|Yes| GrantAccess["Access Granted"]
    CheckPermissions -->|No| Deny["403 Forbidden"]
```

### 3.9 Error Handling & Recovery Flow
Map how errors propagate and are handled:

```
flowchart TD
    Operation --> Error{Error?}
    Error -->|No| Success["Return Result"]
    Error -->|Yes| Classify{"Error Type"}
    Classify -->|Retryable| Retry["Retry with Backoff"]
    Classify -->|Validation| UserError["Return 400"]
    Classify -->|System| Log["Log + Alert"]
    Log --> Fallback["Fallback/Circuit Breaker"]
```

### 3.10 Deployment / Infrastructure Diagram
Map the deployment topology:

```
graph TB
    subgraph "CI/CD"
        Git --> Pipeline --> Build --> Test --> Deploy
    end
    subgraph "Production"
        LB["Load Balancer"] --> App1["App Server 1"]
        LB --> App2["App Server 2"]
        App1 --> DB[(Database)]
        App2 --> DB
        App1 --> Cache[(Redis)]
        App2 --> Cache
    end
```

### 3.11 Event / Message Flow
For event-driven architectures:

```
flowchart LR
    Producer["Service A"] -->|Publish| Queue["Message Queue"]
    Queue -->|Subscribe| Consumer1["Service B"]
    Queue -->|Subscribe| Consumer2["Service C"]
    Consumer1 -->|Emit| Event["Domain Event"]
    Event --> Handler["Event Handler"]
```

### 3.12 Feature Flow Diagrams
For each major feature, a dedicated flow showing the complete user journey:

```
flowchart TD
    Start["User clicks 'Create Post'"]
    Start --> Form["Fill form"]
    Form --> Validate["Client-side validation"]
    Validate -->|Invalid| ShowErrors["Show errors"]
    ShowErrors --> Form
    Validate -->|Valid| Submit["POST /api/posts"]
    Submit --> ServerValidate["Server validation"]
    ServerValidate --> SaveDB["Save to DB"]
    SaveDB --> Notify["Send notifications"]
    Notify --> Response["Return success"]
    Response --> Redirect["Redirect to post"]
```

### 3.13 Class / Interface Hierarchy
For OOP codebases, map inheritance and implementation:

```
classDiagram
    class BaseService {
        +execute()
        +validate()
    }
    class UserService {
        +getUser()
        +createUser()
    }
    BaseService <|-- UserService
```

### 3.14 Build & CI/CD Pipeline Flow
Map the complete build and deployment pipeline:

```
flowchart LR
    Commit --> Lint --> Test --> Build --> Stage --> Approve --> Deploy
```

### 3.15 Third-Party Integration Map
Show all external service integrations and data exchange:

```
graph LR
    App --> Stripe["Stripe (Payments)"]
    App --> SendGrid["SendGrid (Email)"]
    App --> AWS_S3["S3 (Storage)"]
    App --> Auth0["Auth0 (Auth)"]
```

---

## 4. DOCUMENT STRUCTURE

The output `FLOW_DIAGRAMS.md` must follow this structure:

```markdown
# 🔀 Flow Diagrams — [Project Name]

> Auto-generated flow documentation. Last updated: [DATE]
> Tech Stack: [detected stack]
> Total Diagrams: [count]

## Table of Contents
- [System Architecture Overview](#system-architecture-overview)
- [Directory & Module Structure](#directory--module-structure)
- [Component Dependencies](#component-dependencies)
- [Request/Response Flows](#requestresponse-flows)
- [Data Flows](#data-flows)
- [State Machines](#state-machines)
- [Entity Relationships](#entity-relationships)
- [Authentication & Authorization](#authentication--authorization)
- [Error Handling](#error-handling)
- [Deployment & Infrastructure](#deployment--infrastructure)
- [Event / Message Flows](#event--message-flows)
- [Feature Flows](#feature-flows)
- [Class Hierarchies](#class-hierarchies)
- [CI/CD Pipeline](#cicd-pipeline)
- [Third-Party Integrations](#third-party-integrations)
- [Glossary](#glossary)

---

## System Architecture Overview
[Diagram + prose explanation]

## Directory & Module Structure
[Tree + purpose annotations]

... (each section follows)

## Glossary
[Key terms, abbreviations, and their meanings]
```

---

## 5. FORMATTING RULES

1. **Every diagram MUST have a prose explanation** — Never drop a diagram
   without context. Before each diagram, write 2–4 sentences explaining what
   it shows and why it matters.
2. **Use Mermaid syntax** — All diagrams must use fenced code blocks with
   `mermaid` language identifier.
3. **Quote labels with special characters** — Use `id["Label (Info)"]` syntax
   to prevent Mermaid parse errors.
4. **Color-code by concern** — Use Mermaid styles to differentiate layers:
   - Frontend: blue tones
   - Backend/API: green tones
   - Database: orange/amber tones
   - External services: purple tones
   - Security: red tones
5. **Keep diagrams focused** — If a diagram has more than ~15 nodes, split it
   into sub-diagrams.
6. **Link to source files** — After each diagram, add a "Key Files" section
   linking to the relevant source files using markdown file links.
7. **Add a legend** — Include a legend section at the bottom explaining
   diagram conventions used.

---

## 6. ANNOTATION CONVENTIONS

Use these annotations in diagram labels to convey meaning:

| Symbol | Meaning          |
|--------|------------------|
| 🔒     | Auth-protected   |
| ⚡     | Performance-critical |
| 🛡️     | Security boundary |
| 📦     | External package  |
| 🗄️     | Database operation |
| 📡     | Network call      |
| ⏱️     | Async/queued      |
| 🔄     | Retry logic       |
| ⚠️     | Error path        |

---

## 7. QUALITY RULES

1. **NO-FICTION** — Never invent flows, components, or connections that don't
   exist in the codebase. If uncertain, mark with `<!-- VERIFY: ... -->`.
2. **EVIDENCE-BASED** — Every diagram element must be traceable to actual
   source code. Reference file paths.
3. **COMPLETENESS** — Cover all major features, not just the "happy path".
   Include error flows, edge cases, and alternative paths.
4. **ACCURACY** — Verify that arrows point in the correct direction (caller
   to callee, data producer to consumer).
5. **FRESHNESS** — Include a "Last Updated" timestamp. When updating, note
   what changed.
6. **PROGRESSIVE DETAIL** — Start with high-level overview, drill down into
   specifics. Each section should go: Overview → Detail → Deep Dive.

---

## 8. LARGE CODEBASE STRATEGY

For codebases with more than ~50 files or multiple services:

1. **Split into multiple files**:
   - `FLOW_DIAGRAMS.md` — Master index + system-level diagrams
   - `flows/frontend.md` — Frontend-specific flows
   - `flows/backend.md` — Backend-specific flows
   - `flows/data.md` — Data layer flows
   - `flows/[service-name].md` — Per-service flows

2. **Cross-reference** — Use markdown links between flow documents.

3. **Prioritize** — Generate the most valuable diagrams first:
   1. System Architecture Overview (always first)
   2. Request/Response flows for core features
   3. Data flows
   4. Component dependencies
   5. Everything else

---

## 9. TECHNOLOGY-SPECIFIC GUIDANCE

### Web Applications (React, Vue, Angular, Next.js, etc.)
- Map component hierarchy and prop/state flow
- Map routing structure
- Map client-side state management (Redux, Zustand, Pinia, etc.)
- Map API integration layer
- Map SSR/SSG/ISR rendering flows where applicable

### Backend APIs (Express, FastAPI, Django, Spring, etc.)
- Map middleware pipeline
- Map route → controller → service → repository chain
- Map database query patterns
- Map background job flows
- Map caching strategy

### Microservices
- Map inter-service communication (sync/async)
- Map service mesh topology
- Map API gateway routing
- Map circuit breaker patterns
- Map distributed transaction flows (sagas)

### Mobile Apps (React Native, Flutter, Swift, Kotlin)
- Map screen navigation flow
- Map state management
- Map native module bridges
- Map offline/sync patterns

### CLI Tools
- Map command parsing flow
- Map subcommand structure
- Map configuration loading
- Map output formatting pipeline

### Data Pipelines (ETL, Spark, Airflow, etc.)
- Map DAG structure
- Map data transformation stages
- Map scheduling and dependencies
- Map error handling and retry logic

---

## 10. OUTPUT VERIFICATION

After generating diagrams, verify:

- [ ] All Mermaid blocks render without syntax errors
- [ ] All referenced files actually exist in the codebase
- [ ] Diagram arrows accurately reflect code flow direction
- [ ] No orphan nodes (components not connected to anything)
- [ ] Prose explanations match diagram content
- [ ] Table of contents links work correctly
- [ ] Glossary covers all domain-specific terms used in diagrams

---

## 11. UPDATE PROTOCOL

When the codebase changes and diagrams need updating:

1. **Don't regenerate from scratch** — Update only affected diagrams.
2. **Mark changes** — Add a "Changes" note at the top of updated sections.
3. **Preserve history** — Keep a changelog at the bottom of the document.
4. **Verify consistency** — Ensure updated diagrams don't contradict
   unchanged diagrams.

---

## 12. CODEBASE EXPLANATION SYSTEM (CODEBASE_EXPLAINED.md)

Alongside `FLOW_DIAGRAMS.md`, generate `CODEBASE_EXPLAINED.md` — a deeply
detailed teaching document that explains the ENTIRE codebase in plain,
easy-to-understand language with real-life analogies.

Use the template at [resources/CODEBASE_EXPLAINED_TEMPLATE.md](./resources/CODEBASE_EXPLAINED_TEMPLATE.md).

### 12.1 EXPLANATION PHILOSOPHY

1. **Explain like teaching a friend** — Write as if you're sitting next to
   someone who's smart but has never seen this codebase before.
2. **Always start with WHY** — Before explaining WHAT something does, explain
   WHY it exists. What problem does it solve?
3. **Use real-life analogies for EVERY concept** — Every technical concept
   must have a relatable real-world comparison.
4. **Progressive depth** — Start simple, then go deeper. Never dump
   complexity upfront.
5. **No jargon without definition** — Every technical term must be explained
   the first time it appears.
6. **Show the story, not just the facts** — Explain the journey of data,
   requests, and user actions as narratives.

### 12.2 REAL-LIFE ANALOGY RULES

Every major concept MUST include a `🏠 Real-Life Analogy` block. Guidelines:

| Technical Concept | Analogy Domain | Example |
|---|---|---|
| API / Server | Restaurant | "The API is like a waiter — you (the client) tell the waiter what you want, the waiter goes to the kitchen (database), and brings your food (data) back" |
| Database | Filing Cabinet / Library | "The database is like a massive library where every book (record) has a unique catalog number (ID) and is organized by section (table)" |
| Authentication | Building Security | "Auth is like showing your ID badge at a building entrance — the guard (auth middleware) checks if you're allowed in before letting you access any floor (route)" |
| Caching | Sticky Notes | "A cache is like sticky notes on your desk — instead of walking to the filing cabinet every time, you keep frequently used info right in front of you" |
| Middleware | Airport Security | "Middleware is like airport security checkpoints — every passenger (request) must pass through them before reaching the gate (your actual code)" |
| State Management | Whiteboard in Office | "State is like a shared whiteboard — everyone in the team (components) can read it, and when someone updates it, everyone sees the change" |
| Queue / Async | Post Office | "A message queue is like dropping a letter at the post office — you don't wait at the recipient's door; the postal system delivers it when they're ready" |
| Load Balancer | Traffic Cop | "A load balancer is like a traffic cop at a busy intersection — it directs cars (requests) to different lanes (servers) so no single lane gets jammed" |
| Container / Docker | Shipping Container | "Docker is like a shipping container — no matter what's inside, it fits on any ship (server) the same way, making transport predictable" |
| CI/CD Pipeline | Assembly Line | "CI/CD is like a car factory assembly line — each station (stage) does one job (lint, test, build), and only a car that passes every check rolls off the line" |
| Environment Variables | Secret Ingredients | "Env vars are like a chef's secret recipe card — the kitchen (code) follows instructions, but the specific ingredients (passwords, API keys) come from a separate, protected card" |
| WebSocket | Phone Call | "A WebSocket is like a phone call — once connected, both sides can talk freely at any time, unlike HTTP which is like sending letters back and forth" |
| ORM | Translator | "An ORM is like a translator — you speak JavaScript/Python, the database speaks SQL, and the ORM translates between the two so they can communicate" |
| Microservices | Shopping Mall | "Microservices are like stores in a mall — each store (service) does one thing well (shoes, food, electronics), they're independent, but together they serve the customer" |
| Monolith | Swiss Army Knife | "A monolith is like a Swiss Army knife — everything in one tool; convenient to carry but harder to fix if one blade breaks" |
| Git Branching | Parallel Universes | "Git branches are like parallel universes — you create a copy of reality, make changes safely, and merge the good changes back into the main timeline" |
| Event-Driven | Doorbell | "Events are like doorbells — when someone presses it (event fires), you don't have to keep checking the door; the bell tells you someone's there" |
| Error Handling | Safety Net | "Error handling is like a safety net under a trapeze — the performer (code) aims to succeed, but if they fall (error), the net catches them gracefully" |
| Rate Limiting | Bouncer at Club | "Rate limiting is like a bouncer who only lets 100 people in per hour — if you've hit the limit, you wait outside" |
| Dependency Injection | Plug & Play | "DI is like plugging different USB devices into the same port — the laptop (class) doesn't care what's plugged in, as long as it follows the USB standard (interface)" |

### 12.3 EXPLANATION STRUCTURE PER FILE/MODULE

For every important file or module, provide:

```markdown
### 📄 [filename] — [one-line purpose]

**📍 Location:** `path/to/file`
**🎯 Purpose:** [What this file does in 1-2 sentences]
**🤔 Why it exists:** [What problem would arise without it]

🏠 **Real-Life Analogy:**
> [Analogy that makes the purpose instantly clear]

#### What's Inside (Plain English)
[Walk through the file's contents as a story — what happens first,
what happens next, why each piece matters]

#### Key Functions / Classes Explained

| Name | What It Does (Plain English) | Real-Life Equivalent |
|------|------------------------------|---------------------|
| `functionName()` | [Simple explanation] | [Analogy] |

#### How It Connects to Other Parts
[Explain which files call this one, and which files this one calls,
using plain language]

#### Walk-Through Example
[Trace a real scenario through this file step by step]
```

### 12.4 PROGRESSIVE EXPLANATION LEVELS

Every major system/feature gets THREE explanation levels:

#### Level 1 — 🟢 Beginner ("Explain Like I'm 5")
- Use only everyday words
- Heavy use of analogies
- No code shown, only concepts
- Example: "When you click 'Login', it's like showing your library card at
  the front desk. The librarian checks if your card is real, and if it is,
  you're allowed to borrow books."

#### Level 2 — 🟡 Intermediate ("I know some coding")
- Introduce technical terms with definitions
- Show simplified code snippets
- Explain the "how" alongside the "what"
- Example: "The `loginUser()` function takes your email and password, hashes
  the password using bcrypt (a one-way encryption — like putting a letter
  in a shredder, you can't un-shred it), and compares it against the stored
  hash in the database."

#### Level 3 — 🔴 Advanced ("I want the full picture")
- Full technical detail
- Architecture decisions and trade-offs
- Edge cases, performance implications, security considerations
- Example: "Authentication uses JWT with RS256 asymmetric signing. The
  access token has a 15-minute TTL to minimize the blast radius of token
  theft, while the refresh token (stored in an HttpOnly cookie to prevent
  XSS exfiltration) has a 7-day sliding window. Token rotation is enforced
  — each refresh token is single-use, with the family invalidated on reuse
  detection to mitigate replay attacks."

### 12.5 SYSTEM STORYTELLING

For the overall system, write a "Day in the Life" narrative:

```markdown
## 📖 A Day in the Life of [App Name]

Imagine you're [User Persona]. Here's what happens when you...

### Story 1: [Common Action, e.g., "Sign up for an account"]

1. **You open the app** → The browser loads `index.html`, which pulls in
   the React app from `App.jsx`. Think of this like opening the front
   door of a store.

2. **You click 'Sign Up'** → React Router (the store's directory sign)
   sends you to the `SignupPage` component...

3. **You fill in your details** → The form component (`SignupForm.jsx`)
   collects your name, email, and password. It's like filling out a
   membership application form at a gym...

[Continue the entire flow as a narrative story]
```

### 12.6 CONCEPT GLOSSARY WITH EXAMPLES

Build a glossary that doesn't just define — it TEACHES:

```markdown
## 📚 Glossary — Every Term Explained

### API (Application Programming Interface)
**Technical:** A set of rules and protocols that allows software programs
to communicate with each other.
**Plain English:** It's like a restaurant menu — the menu tells you what
you can order (available endpoints), you tell the waiter your order
(send a request), and the kitchen prepares it and sends it back
(response).
**In This Project:** Our API is defined in `src/routes/` and handles
all communication between the frontend and the database.
```

### 12.7 "HOW DOES THIS ACTUALLY WORK?" DEEP DIVES

For every core feature, provide a deep-dive section:

```markdown
## 🔬 Deep Dive: [Feature Name]

### The Problem
[What real-world problem does this feature solve?]

### The Solution (No-Code Version)
[Explain the solution using only analogies and plain English]

### The Solution (With Code)
[Walk through the actual implementation, annotating every important line]

### Step-by-Step Trace
[Number every step from user action to final result]
1. User clicks [button] →
2. Browser calls `handleClick()` in `Component.jsx:L42` →
3. This triggers `apiClient.post('/endpoint')` →
4. Server receives request at `routes/endpoint.js:L15` →
... [continue until the response reaches the user]

### What Could Go Wrong?
[List failure scenarios with plain-English explanations]
| What Fails | Why | What User Sees | How Code Handles It |
|---|---|---|---|
| Database down | Server can't store data | "Something went wrong" error | `catch` block in service returns 503 |

### Common Questions
**Q: Why don't we just [simpler alternative]?**
A: [Honest explanation of the trade-off]
```

### 12.8 PATTERN RECOGNITION TEACHING

Teach the user to recognize patterns used in the codebase:

```markdown
## 🧩 Patterns Used in This Codebase

### Pattern: [Name, e.g., "Repository Pattern"]

🏠 **Analogy:** Think of a repository like a librarian. You ask the
librarian for a book (data) by title (ID). You don't care whether
the librarian gets it from the shelf, the basement, or another branch —
you just get your book. Similarly, the Repository hides whether data
comes from PostgreSQL, Redis, or an API.

**Where it's used:** `src/repositories/`
**Why it's used:** Keeps database logic separate from business logic,
so you can swap databases without rewriting your entire app.
**Files that use this pattern:**
- [UserRepository.js](file:///path) — Handles user data
- [OrderRepository.js](file:///path) — Handles order data
```

### 12.9 "WHAT HAPPENS WHEN..." SCENARIOS

Create scenario-based explanations for common questions:

```markdown
## ❓ What Happens When...

### ...a user submits a form with invalid data?
[Trace the entire validation flow with analogies]

### ...the database goes down?
[Explain error handling, retries, fallbacks]

### ...1000 users hit the same endpoint simultaneously?
[Explain concurrency, queuing, rate limiting]

### ...a hacker tries to inject SQL?
[Explain security measures in plain language]

### ...you deploy a new version?
[Explain the deployment process step by step]
```

### 12.10 CODE BLOCK ANNOTATION STYLE

When showing code, annotate EVERY important line:

```markdown
```javascript
// 📌 This function runs when someone tries to log in
async function loginUser(email, password) {
  // Step 1: Find the user in our database (like looking up a name
  //         in a phone book)
  const user = await db.users.findOne({ email });

  // Step 2: If no user found, stop here (the name isn't in the phone book)
  if (!user) {
    throw new NotFoundError('User not found');
  }

  // Step 3: Check if the password matches (like comparing a key to a lock)
  //         bcrypt.compare doesn't decrypt — it hashes the input and
  //         compares the hashes (one-way check, like a fingerprint)
  const isValid = await bcrypt.compare(password, user.passwordHash);

  // Step 4: Wrong password? Reject. (Wrong key? Door stays locked.)
  if (!isValid) {
    throw new AuthError('Invalid credentials');
  }

  // Step 5: Create a "pass" (JWT token) that proves who they are
  //         This is like getting a wristband at a concert — show it
  //         at any booth and they know you've paid
  const token = jwt.sign({ userId: user.id }, SECRET, { expiresIn: '15m' });

  return { token, user: sanitize(user) };
}
```
```

---

## 13. CODEBASE_EXPLAINED.md DOCUMENT STRUCTURE

The output `CODEBASE_EXPLAINED.md` must follow this structure:

```markdown
# 📖 [Project Name] — Complete Codebase Explained

> Everything you need to understand this project, explained in plain English.
> Last Updated: [DATE]
> Reading Time: ~[X] minutes

## Table of Contents
1. [What Is This Project?](#what-is-this-project)
2. [Who Is It For?](#who-is-it-for)
3. [The Big Picture (30-Second Version)](#the-big-picture)
4. [Tech Stack Explained](#tech-stack-explained)
5. [Project Structure Map](#project-structure-map)
6. [A Day in the Life (Story Mode)](#a-day-in-the-life)
7. [Every File Explained](#every-file-explained)
8. [Core Features Deep Dive](#core-features-deep-dive)
9. [Patterns & Architecture Explained](#patterns--architecture)
10. [What Happens When... (Scenarios)](#what-happens-when)
11. [Glossary](#glossary)
12. [Common Questions](#common-questions)

---

## What Is This Project?
🟢 Beginner | 🟡 Intermediate | 🔴 Advanced
[Three-level explanation]

## The Big Picture
🏠 **Real-Life Analogy:**
> [The entire system explained as one analogy]

... [remaining sections]
```

---

## 14. EXAMPLE INVOCATION

When the user says:
> "Generate flow diagrams for this project"

Execute:
1. Run Phase 1–3 analysis (Section 2)
2. Generate all applicable diagrams (Section 3)
3. Format per document structure (Section 4)
4. Apply formatting rules (Section 5)
5. Generate `CODEBASE_EXPLAINED.md` (Section 12–13)
6. Run output verification (Section 10)
7. Present BOTH documents to the user

When the user says:
> "Explain this codebase" / "Teach me this code"

Execute:
1. Run Phase 1–3 analysis (Section 2)
2. Generate `CODEBASE_EXPLAINED.md` (Sections 12–13) as primary output
3. Generate `FLOW_DIAGRAMS.md` (Sections 3–5) as supporting visual companion
4. Present both documents with the explanation document highlighted

---

## 15. EXPLANATION QUALITY RULES

1. **NO JARGON WITHOUT DEFINITION** — Every technical term must be explained
   in plain English the first time it appears.
2. **EVERY CONCEPT GETS AN ANALOGY** — No exceptions. If you can't think of
   an analogy, you don't understand the concept well enough.
3. **SHOW THE JOURNEY** — Don't just list what files do. Trace a user action
   from click to screen update as a continuous story.
4. **ANSWER THE "WHY"** — For every piece of code, answer "Why does this
   exist?" and "What breaks if we remove it?"
5. **USE EXAMPLES FROM DAILY LIFE** — Restaurants, libraries, post offices,
   airports, schools — use places everyone knows.
6. **BEGINNER-FIRST** — Always start with the simplest explanation. Advanced
   details come AFTER the reader has a mental model.
7. **NO ASSUMED KNOWLEDGE** — Don't assume the reader knows what REST,
   JWT, middleware, ORM, or any other term means. Define everything.
8. **CONNECT THE DOTS** — Explicitly show how each file/function relates to
   others. "This function is called by X, which is triggered when Y happens."
9. **MAKE IT SCANNABLE** — Use headers, bullets, tables, and callout boxes.
   Nobody reads walls of text.
10. **KEEP IT HONEST** — If code is messy, say so gently. If a pattern is
    overkill for the project size, acknowledge it.

---

## 16. ULTIMATE OBJECTIVE

Make any codebase **visually self-explanatory** AND **deeply teachable**.

A developer should be able to open these documents and within minutes:
- **See** how the system works (FLOW_DIAGRAMS.md)
- **Understand** why it works that way (CODEBASE_EXPLAINED.md)
- **Learn** the concepts behind the code (analogies + progressive levels)
- **Trace** any user action from start to finish (stories + deep dives)
- **Know** what every file does and why it exists (file explanations)
- **Recognize** patterns and architecture decisions (pattern teaching)
- **Handle** edge cases and failures (scenario walkthroughs)

A complete beginner should think: *"Oh, THAT's what this code does!"*
An experienced developer should think: *"Now I see how it all fits together."*

**OBSERVE → ANALYZE → TRACE → DIAGRAM → EXPLAIN → TEACH → VERIFY → DELIVER**
